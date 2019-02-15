The API is accessible on the HTTPS service https://ffs-api.zerator.com/
# API Parts
* [Authenticate and register](/Doc/API/v1/Authentication.md)
* [Own account management](/Doc/API/v1/Me.md)
* [Events management](/Doc/API/v1/Events.md)

### Protected resources
Some resources are accessible only if the user is authenticated. We are using a Token system for authentication. The requests must have the header "Authorization" in their HTTP requests.

#### Example

```bash
curl -H 'Authorization: TOKEN' -X GET http://example.com
```