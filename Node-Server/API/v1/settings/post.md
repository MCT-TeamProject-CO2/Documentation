# POST settings

Create a new mail configuration.

**URL** : `/api/v1/settings/`

**Method** : `POST`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## Request Body

The below body is an example of what you could send.

```json
{
    "id": "number",
    "config": {
        "ppmThresholds": {
           "orange": "number",
           "red": "number",
       },
       "disableNormalLogin": "boolean",
   }
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