# GET users

Get all the users that are stored in the DB.

**URL** : `/api/v1/users/`

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
        "disabled": false,
        "_id": "5ff5c4bff45576e12b62f087",
        "email": "email@example.com",
        "username": "Yimura",
        "password": "$2b$10$XgdcN654JrjGzjd0LRzxvucTTYT32kvlKl2qQyY8BrgOyeXUSt3xu",
        "type": "normal",
        "uid": "6140ae10-40a7-42e2-910b-cb996f35854f",
        "__v": 0
    }
]
```