# POST login

This endpoint allows you to create a new session using user credentials.

**URL** : `/api/v1/auth/login/`

**Method** : `POST`

**Auth required** : `NO`

## Request Body

The basic login expecteds at least username & password.

```json
{
    "username": "UserName",
    "password": "Password"
}
```

Alternatively you can use other identifiers to log a user in, these can be used in combination or individually to identify the user.
```json
{
    "uid": "6140ae10-40a7-42e2-910b-cb996f35854f",

    "email": "email@example.com"
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

## Error Response 403

**Condition** : The user could not be found or the password given did not match the one on the server.

**Code** : `403 PERMISSION DENIED`

**Content** :

```json
{
    "code": 403,
    "status": "403 - Permission Denied",
    "message": "The client does not have permission to access the requested resource."
}
```