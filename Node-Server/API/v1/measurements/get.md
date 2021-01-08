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
    "delta": 10
}
```
**Params**:
 - **tagString**
    `Wildcard selector when fetching data. (BCE / BCE.C.0)`
    The tagString syntax goes as follows `location.building.floor.room`.
    Preferably you should fetch `location.building.floor` but depending on your use case this might not fit your needs.
    You can fetch data from an entire location by just passing `location`, or go more in-depth with `location.building`.
 - **delta** (optional = 10)
    `Data to fetch of the last x amount of minutes.`

## Success Response

**Code** : `200 OK`

**Content example**

This endpoint returns a json.
```js
{}
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