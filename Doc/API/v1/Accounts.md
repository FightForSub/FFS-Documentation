# Accounts management

### Endpoints
[GET /accounts/{account_id}](/Doc/API/v1/Accounts.md#get-accountsaccount_id) - Get account informations - Not implemented

[PUT /accounts/{account_id}](/Doc/API/v1/Accounts.md#put-accountsaccount_id) - Update account informations - Not implemented

## `GET /accounts/{account_id}`

Used to retrive account informations. {account_id} must be replaced by the account id.

### Example request

```bash
curl -H 'Content-Type: application/json' -X GET https://xxxx/v1/accounts/42
```

### Example Response

```json
{
  "id": 42,
  "grade": 4000,
  "username": "AlexMog"
}
```

## `PUT /accounts/{account_id}`

Update the informations of the account linked to the {account_id} id. This method can only be used with the Admin grade.

### Example request

```bash
curl -H 'Content-Type: application/json' -X POST -d '{"username":"test","email":"test@test.test","grade":4000}' \
 https://xxxx/v1/accounts/42
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
