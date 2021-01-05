# [`Node-Server`](https://github.com/MCT-TeamProject-CO2/Node-Server)

## Table Of Contents

 - [Introduction](#introduction)
 - [Requirements](#requirements)
 - [Setup](#setup)
 - [Config](#config)
 - [Next Chapter - Modules](#next-chapter-modules)

 ## Introduction

The Node-Server is responsible for providing the following functionality:
 - REST API
 - Sending out alerts (WS)
 - Continuous data update (WS)

It is entirely made to be fully modular without having to rewrite entire parts of the code base. Most of it should just be copy paste from older projects.

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