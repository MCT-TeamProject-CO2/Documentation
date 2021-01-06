# POST login

This endpoint returns all mail configurations.

**URL** : `/api/v1/auth/login/`

**Method** : `POST`

**Auth required** : NO

**Data constraints**

`NOTE`: The data constraints are written as JSON.

```json
{
    "username": "UserName",
    "password": "Password"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

This endpoint returns a json.
```js
{
    // RandomBytes(16).toString('base64')
    "sessionId": "SessionId"
}
```

## Error Response 400

**Condition** : the body is invalid or does not exist

**Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "code": 400,
    "status": "401 - Bad Request",
    "message": "The server did not understand the request, an invalid request body or headers may have been given."
}
```

## Error Response 401

**Condition** : the given password is incorrect

**Code** : `401 UNAUTHORIZED`

**Content** :

```json
{
    "code": 401,
    "status": "401 - Unauthorized",
    "message": "The client failed to authenticate."
}
```