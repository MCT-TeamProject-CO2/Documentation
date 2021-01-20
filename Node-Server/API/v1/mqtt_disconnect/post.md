# POST mqtt_disconnect

Returns all the locations registered in the DB.

**URL** : `/api/v1/mqtt_disconnect/`

**Method** : `POST`

**Auth required** : `NO`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## Request Body

```json
{
    "message": "Error message",
}
```

## Success Response

**Code** : `201 CREATED`

**Content example**

Empty response body.

## Error Response 400

**Condition** : The body contents are invalid or empty.

**Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "code": 400,
    "status": "400 - Bad Request",
    "message": "The server did not understand the request, an invalid request body or headers may have been given."
}
```