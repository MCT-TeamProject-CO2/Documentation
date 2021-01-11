# REST API

## Table of contents

- [Endpoints](#endpoints)
- [Creatin a new endpoint](#creating-a-new-endpoint)
    - [Example endpoint](#example-endpoint)
    - [Route](#route)

## Endpoints

You can view the documentation of each endpoint in the [`API/`](API/) folder. In here we show you what each endpoint required options are. The request body, headers, response codes and what they mean...

[View it here](API/).

## Creating a new endpoint

Creating a new endpoint is really easy, with how the REST API is structured you can just create a new file in the `/api/v1/` folder.
Your endpoint will be registered in the path that you put the file in.
So let's say for example you create a file `/api/v1/users/create.js` then your endpoint's base path will be `/api/v1/users/`.

### Example Endpoint

Ok we know our endpoint's base will be `/api/v1/users/` but how do we set the route of endpoint itself? Well that's pretty easy, just make sure you have a route getter in your class that returns a string representing the path of your endpoint.

```js
import Route from '~/src/structures/routes/Route.js'

/**
 * Route: /api/v1/users/create
 */
export default class CreateUser extends Route {
    constructor(main) {
        super(main);
    }

    get route() {
        return '/create';
    }

    /**
     * Create a new user
     * @param {Request} request 
     */
    async post(request) {
        if (!await this.isSessionValid(request, 'admin')) return request.reject(403);

        const body = await request.json();
        if (!body) return request.reject(400);

        try {
            await this.model.createUser(body);

            return request.accept('', 201);
        } catch (error) {
            console.log(error);

            return request.reject(406, {
                code: 406,
                status: "406 - Not Acceptable",
                message: error.message
            });
        }
    }
}
```

In the above example we can see only one method in our class `#post`, the method name should match method used by a HTTP client to make the request, in theory you could define any number of custom methods.

## Route

In our example code we imported a Route class, this class adds some basic functionality/helpers that we can use to write our code smaller.

```js
export default class Route {
    /**
     * @param {Main} main The program entrypoint class
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
    
    get route() {
        throw new Error('The route of this endpoint has not been defined.');
    }

    /**
     * Checks if a session is valid
     * @param {Request} request
     * @param {string} [permLevel = "info"]
     * @returns {Promise<boolean>}
     */
    isSessionValid(request, permLevel = 'info') {
        return this.modules.session.isSessionValid(request.headers['authorization'], permLevel);
    }
}
```