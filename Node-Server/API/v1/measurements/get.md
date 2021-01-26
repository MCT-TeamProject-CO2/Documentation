# GET measurements

Get the last 10 minutes of measurements for a given location.

**URL** : `/api/v1/measurements/`

**Method** : `GET`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## URL Search Params

`/api/v1/measurements?tagString=BCE.C.0.003&delta=10`
```json
{
    "tagString": "BCE.C.0.003",
    "delta": 10,
    "start" : "unix timestamp",
    "end" : "unix timestamp",
    "fields" : ["field1", "field2", ...],
    "mean" : "boolean",
    "aggregate" : "time string (5s, 5m, ...)"
}
```
**Params**:
 - **tagString**
    `Wildcard selector when fetching data. (BCE / BCE.C.0)`
    The tagString syntax goes as follows `location.building.floor.room`.
    Preferably you should fetch `location.building.floor` but depending on your use case this might not fit your needs.
    You can fetch data from an entire location by just passing `location`, or go more in-depth with `location.building`.
 - **delta** (default = 10)
    `Data to fetch of the last x amount of minutes.`
 - **start**
    `optional` Timestamp from where to start getting measurements.
 - **end**
    `optional` Timestamp till where you want to get the measurements.
 - **field**
    fields to retreive from influx db
 - **mean**
    get mean datapoints or not
 - **aggregate**
    mean length

## Success Response

**Code** : `200 OK`

**Content example**

This endpoint returns a json.
```json
{
    "BCE.C.0.003": [
        {
            "result": "_result",
            "table": 0,
            "_start": "2021-01-20T15:10:30.177Z",
            "_stop": "2021-01-20T15:12:30.192378955Z",
            "_time": "2021-01-20T15:10:32Z",
            "_value": 476,
            "_field": "co2eq_ppm",
            "_measurement": "BCE.C.0.003"
        },
        ...,
        {
            "result": "_result",
            "table": 0,
            "_start": "2021-01-20T15:10:30.177Z",
            "_stop": "2021-01-20T15:12:30.192378955Z",
            "_time": "2021-01-20T15:10:42Z",
            "_value": 481,
            "_field": "co2eq_ppm",
            "_measurement": "BCE.C.0.003"
        }
    ]
}
```

## Error Response 400

**Condition** : The GET request params you gave were invalid.

**Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "code": 400,
    "status": "400 - Bad Request",
    "message": "The server did not understand the request, an invalid request body or headers may have been given."
}
```

## Error Response 403

**Code** : `403 PERMISSION DENIED`

**Condition** : The session id given in the authorization header is invalid, does not exist or has expired.

**Content**

```json
{
    "code": 403,
    "status": "403 - Permission Denied",
    "message": "The client does not have permission to access the requested resource."
}
```