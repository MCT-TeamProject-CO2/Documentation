# GET mqtt_disconnect

Get all error logs from the data handler for the last X minutes or between 2 specific timestamps.

**URL** : `/api/v1/mqtt_disconnect/`

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
    "delta" : "number",
    "start" : "unix timestamp",
    "end" : "unix timestamp"
}
```

**Params**:
 - **delta** (default = 10)
    `Data to fetch of the last x amount of minutes.`
 - **start**
    Timestamp from where to start getting measurements.
 - **end**
    Timestamp till where you want to get the measurements.


## Success Response

**Code** : `200 OK`

**Content example**

This endpoint returns a json.
```json
{
    "_id" : ObjectId("60070da1f042ee16c7a09020"),
    "technical" : "test",
    "level" : "warning",
    "type" : "data_handler",
    "message" : "The Python data handler encountered an error:",
    "datetime" : ISODate("2021-01-19T16:49:37.000Z"),
    "__v" : 0
}
```

## Error Response 400

**Code** : `400 BAD REQUEST`


**Condition** : The GET request params you gave were invalid.

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

**Condition** : The session id given in the authorization header is invalid, does not exist or has expired or your user does not have the required permission level.

**Content**

```json
{
    "code": 403,
    "status": "403 - Permission Denied",
    "message": "The client does not have permission to access the requested resource."
}
```