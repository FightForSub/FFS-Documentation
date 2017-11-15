# Authentication and Register
## Authentication process
The API uses OAuth2 protocol to authenticate users and applications. All users must be authenticated by this protocol aswell as your application (see the [Authentication service documentation](/Doc/AuthenticationService)).

### Endpoints
[POST /account/login](/Doc/API/v1/Authentication.md#post-accountlogin) - Login a new account, if the account is not already registered, will register it  
[DELETE /account/login](/Doc/API/v1/Authentication.md#delete-accountlogin) - Revoke the token (logout the user)
[GET /account/login](/Doc/API/v1/Authentication.md#get-accountlogin) - Validate the email token

## `POST /account/login`

Used to login an user.
If the user is not already registered, an account will be created for him.
It will generate an OAuth token useable for this resource server.

### Example request

```bash
curl -H 'Content-Type: application/json' -X POST -d '{"twitch_token":"TWITCH_TOKEN"}' \
 https://ffs-api.zerator.com/v1/account/login
```

### Example Response

```json
{
  "access_token": "xxxxxxxxxxxx",
  "expires_in": 0,
  "new_account": true
}

```

### Errors

422: A bad entity was passed to the HTTP body. (Not JSON, or missing fields)  
400: Bad authentication.

## `DELETE /account/login`

Used to logout of the API (this action will revoke the OAuth token).

### Example request

```bash
curl -H 'Content-Type: application/json' -X DELETE https://ffs-api.zerator.com/v1/account/login
```

This endpoint always return HTTP code: 204 (No content)

## `GET /account/login`

Used to validate the email.

### Example request

```bash
curl -H 'Content-Type: application/json' -X GET \
 https://ffs-api.zerator.com/v1/account/login?code=EMAIL_CODE
```

### Example Response

```json
{
  "code": 200,
  "description": "The request has succeeded",
  "reasonPhrase": "OK",
  "throwable": null,
  "uri": "http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1",
  "error": false,
  "success": true,
  "informational": false,
  "globalError": false,
  "clientError": false,
  "serverError": false,
  "connectorError": false,
  "redirection": false,
  "recoverableError": false
}

```

### Errors

422: A bad entity was passed to the HTTP body. (Not JSON, or missing fields)  
409: Email already activated
