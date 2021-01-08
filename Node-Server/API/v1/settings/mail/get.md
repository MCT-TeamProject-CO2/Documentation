# GET mail

This endpoint returns all mail configurations.

**URL** : `/api/v1/settings/mail/`

**Method** : `GET`

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

This endpoint returns a json with a list of all available configurations.
```json
[
  {
    "config": {
      "auth": {
        "user": "username",
        "pass": "password"
      },
      "pool": true,
      "host": "smtp.scarlet.be",
      "port": 465,
      "secure": true
    },
    "_id": "5ff496de8319f51c1be09a2c",
    "name": "scarlet",
    "__v": 0
  }
]
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

