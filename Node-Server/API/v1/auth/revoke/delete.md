# DELETE revoke

This endpoint will attempt to revoke any session that is feeded to it, assuming that if you know the session ID it's safe to revoke these.

**URL** : `/api/v1/auth/revoke/`

**Method** : `DELETE`

**Auth required** : `NO`

## Request Body

```json
{
    "sessionId": "<SessionId>"
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