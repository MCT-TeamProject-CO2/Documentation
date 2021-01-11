# Modules

## Table of contents

 - [Base](#base)
 - [Registering](#registering)
 - [Init](#init)
 - [BaseModule](#basemodule)
 - [EventModule](#eventmodule)
 - [Module Referencing](#module-referencing)

## Base

At the start every module starts of the same, you only need two files, in one of these you put your code the other provides the basic functionality that is needed for your module to work with other modules.

`ExampleModule/index.js`
```js
import BaseModule from './structures/BaseModule.js'

export default class Example extends BaseModule {
    /**
     * @param {Main} main The program entrypoint class
     */
    constructor(main) {
        super(main);

        this.register(REST, {
            name: 'example'
        });
    }

    async init() {
        // Code

        return true;
    }
}
```

## Registering

Each module needs to register itself before it can be used, the least that is required for a module to register with is its `name`.
If you scroll back you can see that we used `this.register` in the constructor of our module.

Inside of here you can set what your module requires, what events it listens to and so on...

```js
{
    // The modules reference name
    name: 'mail',

    // Other modules that are needed for this module to operate normally
    requires: [ 'mongo' ],

    // Events that this module listens directly for
    events: [
        {
            // The module that provides the event
            mod: 'mongo',
            // The name of the event that should be listened on
            name: 'ready',
            // The function to call "this._updateConfiguration(...args)"
            call: '_updateConfigurations'
        }
    ]
}
```

## Init

Every module can provide an init method, this method ensures that other module instances have been setup, if you think that this may be too early to access another module think of using events to trigger an action in your module. You may assume that it's safe to access methods and properties from other modules. This method is also awaited so there's no harm to making this method asyncronous. This method expects you to return a boolean, if you return false the entire applications process will be halted, so make sure to return true as returning nothing may create unexpected behaviour.

**This method is optional, you don't need one in your module.**

## BaseModule

All modules need to at least extend the BaseModule class, it provides critical functionality for your module to operate normally, if you don't extend on this class your code may not run at all.

`ExampleModule/structures/BaseModule.js`
```js
export default class BaseModule {
    /**
     * @param {Main} main
     */
    constructor(main) {
        this._m = main;
    }

    get auth() {
        return this._m.auth;
    }

    get config() {
        return this._m.config;
    }

    get log() {
        return this._m.log;
    }

    get modules() {
        return this._m.modules;
    }

    /**
     * @param {Object} object
     * @param {boolean} internal If this is the raw register object
     */
    register(instance, object, internal = true) {
        if (typeof object !== 'object') throw new Error('Invalid self assignment, expected object but got different type instead.');

        Object.assign(this, object);

        if (internal) {
            this.instance = instance;

            delete object.category;
            this.rawData = object;
        }
        else if (this.rawData) {
            Object.assign(this.rawData, object);
        }
    }
}
```

The following BaseModule class may become outdated over time, make sure if this code is still the same, preferably copy the code from [here](https://github.com/MCT-TeamProject-CO2/Node-Server/blob/main/src/modules/Mail/structures/BaseModule.js).

## EventModule

The EventModule base class exists for if you need to create a module that can emit events, the code of the class about the same only that it extends the [EventEmitter class from events](https://nodejs.org/api/events.html#events_class_eventemitter).

```js
import { EventEmitter } from 'events';

export default class BaseModule extends EventEmitter {
    /**
     * @param {Main} main
     */
    constructor(main) {
        super();

        this._m = main;
    }

    get auth() {
        return this._m.auth;
    }
    
    get config() {
        return this._m.config;
    }

    get log() {
        return this._m.log;
    }

    get modules() {
        return this._m.modules;
    }

    /**
     * @param {Object} object
     * @param {boolean} internal If this is the raw register object
     */
    register(instance, object, internal = true) {
        if (typeof object !== 'object') throw new Error('Invalid self assignment, expected object but got different type instead.');

        Object.assign(this, object);

        if (internal) {
            this.instance = instance;

            delete object.category;
            this.rawData = object;
        }
        else if (this.rawData) {
            Object.assign(this.rawData, object);
        }
    }
}
```

This code example may become outdated as well over time, make sure the code is up to date and preferably copy it from [here](https://github.com/MCT-TeamProject-CO2/Node-Server/blob/main/src/modules/MongoDB/structures/EventModule.js).

## Module Referencing

The great thing about modules is that they're all co-accessible, you can call method from other modules, access properties, etc...

We'll go back to the example I gave at the beginning of the file, I'll give an example of 2 different modules side by side and how you can access their methods.

`ExampleModule/index.js`
```js
import BaseModule from './structures/BaseModule.js'

export default class Example extends BaseModule {
    /**
     * @param {Main} main The program entrypoint class
     */
    constructor(main) {
        super(main);

        this.register(REST, {
            name: 'example',
            requires: [ 'another' ],
            events: [
                {
                    mod: 'another',
                    name: 'ready',
                    call: '_anotehrModReady'
                }
            ]
        });
    }

    /**
     * @private
     */
    _anotherModReady() {
        // Since our "another" module sent out its ready event we are sure
        // it has initialized fully and we can access its special method.

        // You can access other modules through
        // this.modules."module name".some_function()
        this.modules.another.query('SELECT * FROM somedata');
    }

    /**
     * @returns {boolean}
     */
    init() {
        // Do Some Cool stuff
        this.log.info('EXAMPLE', 'Module is ready.')

        return true;
    }
}
```

But instead this module extends the EventModule class allowing for it to  emit events and other modules to listen for these.
`AnotherModule/index.js`
```js
import EventModule from './structures/EventModule.js'

export default class Example extends EventModule {
    /**
     * @param {Main} main The program entrypoint class
     */
    constructor(main) {
        super(main);

        this.register(REST, {
            name: 'another'
        });
    }

    /**
     * @param {*} q
     */
    async query(q) {
        // think that this module does something fancy
        this.conn.query(q);
    }

    async init() {
        // make some connection to a database
        this.conn = await callSomeConnectionFunction();

        this.emit('ready');

        return true;
    }
}
```

<hr/>

#### [`Next Chapter - REST API =>`](./2-REST.md)