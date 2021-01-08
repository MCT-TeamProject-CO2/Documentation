# GET locations

Returns all the locations registered in the DB.

**URL** : `/api/v1/locations/`

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
```js
[
    {
        "_id": "5ff74c9c92c0551b9b346937",
        "name": "Howest Kortrijk Weide",
        "tag": "KWE",
        "buildings": [
            {
                "_id": "5ff74c9c92c05580cb346938",
                "name": "Gebouw A",
                "tag": "A",
                "floors": [
                    {
                        "_id": "5ff74c9c92c055564e346939",
                        "name": "Gelijkvloers",
                        "tag": "0",
                        "rooms": [
                            {
                                "_id": "5ff74c9c92c055d4e634693a",
                                "name": "104",
                                "tag": "104"
                            }
                        ]
                    }
                ]
            }
        ],
        "__v": 0
    },
    {
        "_id": "5ff76a200050401807bcdc7b",
        "name": "Howest Brugge Centrum",
        "tag": "BCE",
        "buildings": [
            {
                "_id": "5ff76a2000504013f9bcdc7c",
                "name": "Gebouw C",
                "tag": "C",
                "floors": [
                    {
                        "_id": "5ff76a20005040e29abcdc7d",
                        "name": "Gelijkvloers",
                        "tag": "0",
                        "rooms": [
                            {
                                "_id": "5ff76a2000504058efbcdc7e",
                                "name": "003",
                                "tag": "003"
                            },
                            {
                                "_id": "5ff76a200050404181bcdc7f",
                                "name": "004",
                                "tag": "004"
                            }
                        ]
                    }
                ]
            }
        ],
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