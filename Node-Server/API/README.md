# RESTAPIDocs

This documentation example is written from the standpoint that your server is running under http://localhost:8080. Modify your URL's accordingly when implementing your own interface.

Currently the API is on its first revision, there will be no differentiation until a newer version is released.

## Open Endpoints

Open endpoints require no Authentication.

- [Auth](v1/auth/)
    - [`POST /api/v1/auth/login/`](v1/auth/login/post.md)
    - [`POST /api/v1/auth/oauth2/`](v1/auth/oauth2/post.md)
    - [`DELETE /api/v1/auth/revoke/`](v1/auth/revoke/delete.md)
    - [`GET /api/v1/auth/valid/`](v1/auth/valid/get.md)

## Closed Endpoints

Closed endpoints **require** Authentication.

- [Alerts](v1/alerts/)
    - [`GET /api/v1/alerts/`](v1/alerts/get.md)
- [Locations](v1/locations/)
    - [`GET /api/v1/locations/`](v1/locations/get.md)
    - [`POST /api/v1/locations/`](v1/locations/post.md)
    - [`PUT /api/v1/locations/`](v1/locations/put.md)
- [Measurements](v1/measurements/)
    - [`GET /api/v1/measurements/`](v1/measurements/get.md)
- [MQTT Disconnect](v1/mqtt_disconnect/)
    - [`GET /api/v1/mqtt_disconnect/`](v1/mqtt_disconnect/get.md)
    - [`POST /api/v1/mqtt_disconnect/`](v1/mqtt_disconnect/post.md)
- [Settings](v1/settings/)
    - [`GET /api/v1/settings/`](v1/settings/get.md)
    - [`POST /api/v1/settings/`](v1/settings/post.md)
- [Settings/Mail](v1/settings/mail/)
    - [`DELETE /api/v1/settings/mail`](v1/settings/mail/delete.md)
    - [`GET /api/v1/settings/mail`](v1/settings/mail/get.md)
    - [`POST /api/v1/settings/mail`](v1/settings/mail/post.md)
- [Users](v1/users/)
    - [`DELETE /api/v1/users/`](v1/users/delete.md)
    - [`GET /api/v1/users/`](v1/users/get.md)
    - [`POST /api/v1/users/`](v1/users/post.md)
    - [`PUT /api/v1/users/`](v1/users/put.md)
- [Smart Plugs](v1/smartplugs/)
    - [`POST /api/v1/smartplugs/`](v1/smartplugs/post.md)
- [Mail](v1/mail/)
    - [`DELETE /api/v1/mail/`](v1/mail/delete.md)
    - [`GET /api/v1/mail/`](v1/mail/get.md)
    - [`POST /api/v1/mail/`](v1/mail/post.md)