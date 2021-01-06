# DELETE mail

This endpoint returns all mail configurations.

**URL** : `/api/v1/settings/mail/`

**Method** : `DELETE`

**Auth required** : YES

**Data constraints**

`NOTE`: The data constraints are written as JSON

```json
{
    "Authorization": "SessionId"
}
```

## Success Response

**Code** : `202 ACCEPTED`

This endpoint does not return json.

## Error Response 400

**Condition** : if the body is invalid or does not exist

**Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "code": 400,
    "status": "400 - Bad Request",
    "message": "The server did not understand the request, an invalid request body or headers may have been given."
}
```