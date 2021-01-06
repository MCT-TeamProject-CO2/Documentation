# POST mail

This endpoint returns all mail configurations.

**URL** : `/api/v1/settings/mail/`

**Method** : `POST`

**Auth required** : YES

**Data constraints**

`NOTE`: The data constraints are written as JSON

```json
{
    "Authorization": "SessionId"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

This endpoint returns a json.
```json
{
    "success": true
}
```

If the configuration already exist the following will be returned
```json
{
    "success": false,
    "message": "There already exists a mail configuration with the given name."
}
```

## Error Response 400

**Condition** : If no 'url' was passed in the URLSearchParams.

**Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "code": 400,
    "status": "400 - Bad Request",
    "message": "The server did not understand the request, an invalid request body or headers may have been given."
}
```