# GET search

Get the last 10 minutes of measurements for a given location.

**URL** : `/api/v1/measurements/search/`

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
    "q": "influx query"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

This endpoint returns a json.
```json
{
    result depending on query
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