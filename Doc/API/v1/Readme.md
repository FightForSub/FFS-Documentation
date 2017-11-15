The API is accessible on the HTTPS service https://XXX/
# API Parts
* [Authenticate and register](/Doc/API/v1/Authentication.md)
* [Own account management](/Doc/API/v1/Me.md)

### Protected resources
Some resources are accessible only if the user is authenticated. We are using OAuth2 protocol for authentication. The requests must have the header "Authorization" in their HTTP requests.

#### Example

```bash
curl -h 'Authorization: OAUTH_TOKEN' -X GET http://example.com
```