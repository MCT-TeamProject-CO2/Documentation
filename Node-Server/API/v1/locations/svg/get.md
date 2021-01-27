# GET svg

Returns all the locations registered in the DB.

**URL** : `/api/v1/locations/svg/`

**Method** : `GET`

**Auth required** : `NO`

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
    "svg": "svg in string format"
}
```

## Error Response 400

**Condition** : The body contents are invalid or empty.

**Code** : `400 BAD REQUEST`

**Content** 

```json
{
    "code": 400,
    "status": "400 - Bad Request",
    "message": "The server did not understand the request, an invalid request body or headers may have been given."
}
```