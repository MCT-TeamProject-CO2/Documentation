# DELETE mail

This endpoint returns all mail configurations.

**URL** : `/api/v1/settings/mail/`

**Method** : `DELETE`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## Success Response

**Code** : `202 ACCEPTED`

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