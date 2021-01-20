# GET alerts

Get alerts for a given time period/delta.

**URL** : `/api/v1/alerts/`

**Method** : `GET`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## URL Search Params

`/api/v1/measurements?delta=20`
```json
{
    "delta": 20
}
```
**Params**:
 - **delta** (default = 20)
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
[
    {
        "_id" : "60077160bf377da71a7781aa",
        "code" : 1,
        "tagString" : "BCE.C.0.003",
        "co2" : 450.271347248577,
        "humidity" : 23.7946613282732,
        "temperature" : 26.47770113852,
        "tvoc" : 7.11764705882353,
        "createdAt" : "2021-01-19T23:55:12.898Z",
        "updatedAt" : "2021-01-19T23:55:12.898Z",
        "__v" : 0
    }
]
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