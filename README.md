# Documentation

Each and every project will be explained in their respective chapter.

## Table Of Contents

- [Basic Setup](#basic-setup)
- [DataHandling](#datahandling)
- [Frontend](#frontend)
- [Node-Server](#nodeserver)

## Basic Setup

For a setup of all the services refer to the [setup repository](https://github.com/MCT-TeamProject-C02/Setup.git).

## DataHandling

The [Datahandling](https://github.com/MCT-TeamProject-CO2) is responsible for collecting all the data from sensors and push these to our InfluxDB instance.

## Frontend

The [Frontend](https://github.com/MCT-TeamProject-CO2) project only contains static files and should be served with a static webserver (like Apache, nginx, ...).

## Node-Server

The [Node-Server](https://github.com/MCT-TeamProject-CO2) is responsible for serving the REST API as well as create alerts on the frontend or send out custom alerts over e-mail, sms, Teams chat, etc...