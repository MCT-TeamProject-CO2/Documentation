# [`DataHandling`](https://github.com/MCT-TeamProject-CO2/DataHandling)

## Table Of Contents

 - [Introduction](#introduction)
 - [Requirements](#requirements)
 - [Setup](#setup)
 - [Config](#config)

 ## Introduction

 The Data Handler is written in Python and receives data from an MQTT broker and stores these in an InfluxDB

 ## Requirements

- Python 3
    - paho-mqtt
    - influxdb-client

## Setup

##### Clone Project

```sh
git clone https://github.com/MCT-TeamProject-CO2/DataHandling.git
```

## Config

There is an example Config file [`config/config.ini.example`](https://github.com/MCT-TeamProject-CO2/DataHandling/blob/master/config/config.ini.example) which you can modify using the information below and then remove the **.example** extension.

### Influx Config
* **token**: InfluxDB Access Token
* **url**: Hostname or IP address of InfluxDB
* **org**: Organization Name in InfluxDB
* **bucker**: Bucket Name (similar to a table) that will hold the data
### MQTT Config
* **topic**: topic to subscribe to
* **host**: Hostname or IP address of the MQTT broker

