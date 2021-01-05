# [`Node-Server`](https://github.com/MCT-TeamProject-CO2/Node-Server)

## Table Of Contents

 - [Introduction](#introduction)
 - [Requirements](#requirements)
 - [Setup](#setup)
 - [Config](#config)
 - [Next Chapter - Modules](#next-chapter-modules)

 ## Introduction

 The Node server is made to be modular by design, it uses a module loader to dynamically load modules and let these interact with each other in an easy to understand and interactive way.

 ## Requirements

- NodeJS v14+

`(docker uses node:15-buster)`

## Setup

##### Clone Project

```sh
git clone https://github.com/MCT-TeamProject-CO2/Node-Server.git
```

##### Starting the code

```bash
# just using node
node --experimental-loader=./util/loader.js .

# or through npm
npm start

# or using docker-compose
docker-compose build && docker-compose up
```

## Config

Don't forgot to modify [`data/auth.js`](https://github.com/MCT-TeamProject-CO2/Node-Server/blob/main/data/auth.js) and [`data/config.js`](https://github.com/MCT-TeamProject-CO2/Node-Server/blob/main/data/config.js), these may need to be modified depending on your deployment configuration.

<hr/>

#### [`Next Chapter - Modules =>`](./1-Modules.md)