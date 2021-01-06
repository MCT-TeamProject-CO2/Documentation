# POST oauth2

This endpoint returns all mail configurations.

**URL** : `/api/v1/auth/oauth2/`

**Method** : `POST`

**Auth required** : YES

**Data constraints**

`NOTE`: The data constraints are written as JSON.

```json
{
    "code": "0.AQUAsUvtTf9rs0Ku..."
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

If the configuration already exist the following will be returned
```json
{
    "success": false,
    "message": "There already exists a mail configuration with the given name."
}
```

## Error Response 404

**Condition** : if no user was found matching this microsoft account

**Code** : `404 NOT FOUND`

**Content** :

```json
{
    "code": 400,
    "status": "400 - Bad Request",
    "message": "The server did not understand the request, an invalid request body or headers may have been given."
}
```

## Error Response 406

**Condition** : 

**Code** : `406 NOT ACCEPTABLE`

**Content** : This is returned by microsoft's endpoint: https://graph.microsoft.com/v1.0/me

```json
{
    "code": 406,
    "status": "406 - Not Acceptable",
    "data": {
        "error": "invalid_grant",
        "error_description": "AADSTS70000: The provided value for the 'code' parameter is not valid. The code has expired.\r\nTrace ID: b4b745da-baba-40fd-8c05-0624cedc5900\r\nCorrelation ID: 8174bc34-c573-4133-bb62-0ff783c7a055\r\nTimestamp: 2021-01-06 17:33:22Z",
        "error_codes": [
            70000
        ],
        "timestamp": "2021-01-06 17:33:22Z",
        "trace_id": "b4b745da-baba-40fd-8c05-0624cedc5900",
        "correlation_id": "8174bc34-c573-4133-bb62-0ff783c7a055",
        "error_uri": "https://login.microsoftonline.com/error?code=70000"
    }
}
```