# RESTAPIDocs

This documentation example is written from the standpoint that your server is running under http://localhost:8080. Modify your URL's accordingly when implementing your own interface.

Currently the API is on its first revision, there will be no differentiation until a newer version is released.

## Open Endpoints

Open endpoints require no Authentication.

- [Auth](v1/auth/)
    - [`POST /api/v1/auth/login/`](v1/auth/login/post.md)
    - [`POST /api/v1/auth/oauth2/`](v1/auth/oauth2/post.md)
    - [`DELETE /api/v1/auth/revoke/`](v1/auth/revoke/delete.md)

## Closed Endpoints

Closed endpoints **require** Authentication.

- [Locations](v1/locations/)
    - [`GET /api/v1/locations/`](v1/locations/get.md)
    - [`POST /api/v1/locations/`](v1/locations/post.md)
- [Measurements](v1/location/)
    - [`GET /api/v1/measurements/`](v1/measurements/get.md)
- [Settings](v1/measurements/)
    - [`DELETE /api/v1/settings/mail`](v1/settings/mail/delete.md)
    - [`GET /api/v1/settings/mail`](v1/settings/mail/get.md)
    - [`POST /api/v1/settings/mail`](v1/settings/mail/post.md)

    - [`DELETE /api/v1/settings/sms`](v1/settings/sms/delete.md)
    - [`GET /api/v1/settings/sms`](v1/settings/sms/get.md)
    - [`POST /api/v1/settings/sms`](v1/settings/sms/post.md)
- [Users](v1/users/)
    - [`DELETE /api/v1/users/`](v1/users/delete.md)
    - [`GET /api/v1/users/`](v1/users/get.md)
    - [`POST /api/v1/users/`](v1/users/post.md)
    - [`PUT /api/v1/users/`](v1/users/put.md)