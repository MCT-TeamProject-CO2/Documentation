# POST users

Create a new user in the DB.

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

```js
{
    email: { type: String, required: true, unique: true },
    type: { type: String, required: true, enum: AccountTypes },
    username: { type: String, unique: true },
    password: String
}

// AcountTypes
const AccountTypes = ['normal', 'oauth2'];
```

Example Body:
```json
{
    "email": "email@example.com",
    "type": "normal",
    "username": "example",
    "password": "password"
}
```
If the account type is set to `oauth2`, you can omit the `username`  and `password` fields in the user object.

Passwords are hashed right before the user object is inserted.

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

## Error Response 406

**Condition** : The body contents are invalid or empty.

**Code** : `406 NOT ACCEPTABLE`

**Content** :

```json
{
    "code": 406,
    "status": "406 - Not Acceptable",
    "message": "An error specific to the creation/insertion of the user in the DB."
}
```
