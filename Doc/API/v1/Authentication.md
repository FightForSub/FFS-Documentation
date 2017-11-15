# Authentication and Register
## Authentication process
The API uses OAuth2 protocol to authenticate users and applications. All users must be authenticated by this protocol aswell as your application (see the [Authentication service documentation](/Doc/AuthenticationService)).

### Endpoints
[POST /account/login](/Doc/API/v1/Authentication.md#post-accountlogin) - Login a new account, if the account is not already registered, will register it - Not implemented yet

[POST /account/logout](/Doc/API/v1/Authentication.md#get-accountlogout) - Revoke the token (logout the user) - Implemented

## `POST /account/login`

Used to login an user.
If the user is not already registered, an account will be created for him.
It will generate an OAuth token useable for this resource server.

### Example request

```bash
curl -H 'Content-Type: application/json' -X POST -d '{"twitch_token":"TWITCH_TOKEN"}' \
 https://xxxx/v1/account/login
```

### Example Response

```json
{
  "access_token": "xxxxxxxxxxxx",
  "token_type": "bearer",
  "scope": "read_user write_user",
  "expires_in": 0
}

```

### Errors

422: A bad entity was passed to the HTTP body. (Not JSON, or missing fields)  
400: Bad authentication.

## `GET /account/logout`

Used to logout of the API (this action will revoke the OAuth token).

### Example request

```bash
curl -H 'Content-Type: application/json' -X GET https://xxx/v1/account/logout
```

This endpoint always return HTTP code: 204 (No content)