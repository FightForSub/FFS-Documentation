The API is accessible on the HTTPS service https://ffs-api.zerator.com/
# API Parts
* [Authenticate and register](/Doc/API/v1/Authentication.md)
* [Own account management](/Doc/API/v1/Me.md)
* [Events management](/Doc/API/v1/Events.md)

### Protected resources
Some resources are accessible only if the user is authenticated. We are using OAuth2 protocol for authentication. The requests must have the header "Authorization" in their HTTP requests.

#### Example

```bash
curl -h 'Authorization: OAUTH_TOKEN' -X GET http://example.com
```