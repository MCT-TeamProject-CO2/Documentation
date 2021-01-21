# POST smarplugs

updates the smart plugs connected to the tp-link account.

**URL** : `/api/v1/smartplugs/`

**Method** : `POST`

**Auth required** : `YES`

## Headers

```json
{
    "Authorization": "SessionId"
}
```

## Success Response

**Code** : `200 ACCEPTED`

**Content example**

Empty response body.


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

**Condition** : update of devices has failed, this could be caused by a connection issue to tp-link.

**Code** : `406 NOT ACCEPTABLE`

**Content** :

```json
{
    "code": 406,
    "status": "406 - Not Acceptable",
    "message": "An error specific to the update of the devices in the node server."
}
```