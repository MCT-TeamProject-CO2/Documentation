# POST locations

Returns all the locations registered in the DB.

**URL** : `/api/v1/locations/`

**Method** : `POST`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## Request Body

```json
{
    "name": "Howest Brugge Centrum",
    "tag": "BCE",
    "buildings": [
        {
            "name": "Gebouw C",
            "tag": "C",
            "floors": [
                {
                    "name": "Gelijkvloers",
                    "tag": "0",
                    "rooms": [
                        {
                            "name": "003",
                            "tag": "003"
                        },
                        {
                            "name": "004",
                            "tag": "004"
                        }
                    ]
                }
            ]
        }
    ]
}
```

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
    "message": "An error specific to the creation/insertion of the user in the DB."
}
```