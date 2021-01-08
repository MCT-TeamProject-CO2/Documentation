# POST mail

Create a new mail configuration.

**URL** : `/api/v1/settings/mail/`

**Method** : `POST`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## Request Body

More information on specific settings for the request body can be found [here](https://nodemailer.com/smtp/).

The below body is an example of what you could send.

```json
{
    "name": "<configuration name>",
    "config": {
        "pool": true,
        "host": "smtp.example.com",
        "port": 465,
        "secure": true,
        "auth": {
            "user": "username",
            "pass": "password"
        }
    }
}
```

## Success Response

**Code** : `200 OK`

**Content example**

This endpoint returns a json.
```json
{
    "success": true
}
```

If the configuration already exist the following will be returned
```json
{
    "success": false,
    "message": "There already exists a mail configuration with the given name."
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