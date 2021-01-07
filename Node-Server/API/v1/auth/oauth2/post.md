# POST oauth2

This endpoint allows you to change an Microsoft OAUTH2 code to create a new session. Under the hood this endpoint will try to match the email returned by the Microsoft to one in the DB.

**URL** : `/api/v1/auth/oauth2/`

**Method** : `POST`

**Auth required** : `YES`

## Request Body

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

**Condition** : If no user was found matching the Microsoft account you're trying to sign in.

**Code** : `404 NOT FOUND`

**Content** :

```json
{
    "code": 404,
    "status": "404 - Not Found",
    "message": "The requested resource has not been found."
}
```

## Error Response 406

**Condition** : This error may occur if somewhere along the OAUTH2 flow an error occurred, there may also be an additional data key in the JSON response body.

**Code** : `406 NOT ACCEPTABLE`

**Content** : 

```json
{
    "code": 406,
    "status": "406 - Not Acceptable",
    "message": "After Processing the Request Body the server did not find the content that was needed to complete the request.",
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