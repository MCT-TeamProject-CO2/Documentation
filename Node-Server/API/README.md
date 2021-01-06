# RESTAPIDocs

This documentation example is written from the standpoint that your server is running under http://localhost:8080. Modify your URL's accordingly when implementing your own interface.

Currently the API is on its first revision, there will be no differentiation until a newer version is released.

## Open Endpoints

Open endpoints require no Authentication.

- [Login](v1/auth/login/)
    - [`POST /api/v1/auth/login/`](v1/auth/login/post.md)
- [Microsoft OAUTH2](v1/auth/oauth2/)
    - [`POST /api/v1/oauth2/`](v1/auth/oauth2/post.md)
- [Revoke](v1/auth/oauth2/)
    - [`GET /api/v1/auth/revoke/`](v1/auth/revoke/delete.md)

## Closed Endpoints

Closed endpoints **require** Authentication.

- [Settings](v1/settings/)
    - [`GET /api/v1/settings/mail`](v1/settings/mail/get.md)
    - [`POST /api/v1/settings/mail`](v1/settings/mail/post.md)
    - [`DELETE /api/v1/settings/mail`](v1/settings/mail/delete.md)
- [Users](v1/users/)
    - [`DELETE /api/v1/users/`](v1/users/delete.md)
    - [`GET /api/v1/users/`](v1/users/get.md)
    - [`POST /api/v1/users/`](v1/users/post.md)
    - [`PUT /api/v1/users/`](v1/users/put.md)