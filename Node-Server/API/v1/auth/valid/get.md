# GET valid

Check if a session id is still valid, this endpoint should not be relied on.
Other endpoints will return 403 so spoofing what this endpoint returns will not aid bad actors.

**URL** : `/api/v1/valid/`

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
    "valid": true
}
```