# DELETE users

This endpoint does not delete users but instead just disables their access rights. The user will be notified of this by mail.

**URL** : `/api/v1/users/`

**Method** : `DELETE`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

Returns the new user profile.
```json
{
    "disabled": true,
    "_id": "5ff5c4bff45576e12b62f087",
    "email": "email@example.com",
    "username": "Yimura",
    "password": "$2b$10$XgdcN654JrjGzjd0LRzxvucTTYT32kvlKl2qQyY8BrgOyeXUSt3xu",
    "type": "normal",
    "config": {
            "mailNotifications": "boolean",
            "smsNotifications": "boolean"
        },
    "uid": "6140ae10-40a7-42e2-910b-cb996f35854f",
    "__v": 0
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