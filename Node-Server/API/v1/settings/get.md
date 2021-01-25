# GET settings

get the existing configuration.

**URL** : `/api/v1/settings/`

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

This endpoint returns a json.
```json
{
    "_id" : "60018eaf9dea72633711516c",
    "config" : {
        "ppmThresholds" : {
            "orange" : "300",
            "red" : "1500"
        },
        "disableNormalLogin" : false
    },
    "id" : 1,
    "__v" : 0
}
```

## Error Response 403

**Code** : `403 PERMISSION DENIED`

**Condition** : The session id given in the authorization header is invalid, does not exist or has expired or your user does not have the required permission level.

**Content**

```json
{
    "code": 403,
    "status": "403 - Permission Denied",
    "message": "The client does not have permission to access the requested resource."
}
```