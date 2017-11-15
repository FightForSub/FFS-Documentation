# Own account management
## Endpoints
[GET /me](/Doc/API/v1/Me.md#get-me) - Get the account informations - Not implemented

[PUT /me](/Doc/API/v1/Me.md#put-me) - Update account informations - Not implemented

## `GET /me`

Get the account informations

### Example request

```bash
curl -H 'Content-Type: application/json' -X GET https://xxxx/v1/me
```

### Example Response

```json
{
  "id": 42,
  "grade": 4000,
  "username": "AlexMog",
  "last_login": 0,
  "email": "XXX@XXX.XXX"
}
```

## `PUT /me`

Update account informations

### Example request

```bash
curl -H 'Content-Type: application/json' -X PUT  -d '{"username":"test","email":"test@test.test","current_password":"current_password"}' https://xxxx/v1/me
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
