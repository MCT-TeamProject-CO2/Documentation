# PUT users

Update a user's profile in the DB.

**URL** : `/api/v1/users/`

**Method** : `POST`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## Request Body

The request body needs to contain a query to match a user and an update object for the properties that should be changed/added to the user.
```json
{
    "query": {
        "email": "email@example.com",
    },
    "update": {
        "old_password": "theOldPlainTextPassword",
        "password": "aNewPlainTextPassword"
    }
}
```
When making an update to the password property you have to provide the old_password as a check.

## Success Response

**Code** : `200 OK`

**Content example**

This endpoint returns the updated user object after modifying it.
```json
{
    "email": "email@example.com",
    ...,
    "type": "normal"
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

## Error Response 406

**Condition** : The body contents are invalid or empty.

**Code** : `406 NOT ACCEPTABLE`

**Content** :

```json
{
    "code": 406,
    "status": "406 - Not Acceptable",
    "message": "An error specific to the creation/update of the user in the DB."
}
```
