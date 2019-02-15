# Events management
## Endpoints
[GET /events](/Doc/API/v1/Events.md#get-events) - Get events list by status  
[POST /events](/Doc/API/v1/Events.md#post-events) - Create a new event  

[GET /event/{EVENT_ID}](/Doc/API/v1/Events.md#get-event) - Get event data  
[PUT /event/{EVENT_ID}](/Doc/API/v1/Events.md#put-event) - Update an event  
[DELETE /event/{EVENT_ID}](/Doc/API/v1/Events.md#delete-event) - Remove an event  

[GET /event/{EVENT_ID}/users](/Doc/API/v1/Events.md#delete-event) - Get registered users on the event  
[POST /event/{EVENT_ID}/users](/Doc/API/v1/Events.md#delete-event) - Register a new user to the event  

[GET /event/{EVENT\\_ID}/user/{USER\\_ID}](/Doc/API/v1/Events.md#delete-event) - Get registered user's data  
[PUT /event/{EVENT\\_ID}/user/{USER\\_ID}](/Doc/API/v1/Events.md#delete-event) - Update registered user's data  
[DELETE /event/{EVENT\\_ID}/user/{USER\\_ID}](/Doc/API/v1/Events.md#delete-event) - Remove registered user  

[GET /event/{EVENT_ID}/rounds](/Doc/API/v1/Events.md#get-events-rounds) - Get event rounds  
[POST /event/{EVENT_ID}/rounds](/Doc/API/v1/Events.md#get-events-rounds) - Add a new round to the event  

[GET /event/{EVENT\\_ID}/round/{ROUND\\_ID}](/Doc/API/v1/Events.md#get-events-round) - Get a round data from the event  
[DELETE /event/{EVENT\\_ID}/round/{ROUND\\_ID}](/Doc/API/v1/Events.md#get-events-round) - Remove the round from the event  

[PUT /event/{EVENT\\_ID}/round/{ROUND\\_ID}/score/{USER\\_ID}](/Doc/API/v1/Events.md#get-events-round) - Updates the user's score on this round  

## `GET /events`

Get events by status.

### Example request

```bash
curl -H 'Content-Type: application/json' -X GET \
 https://ffs-api.zerator.com/v1/events?status=OPEN&start=0&end=50
```

'status' values: OPEN, CLOSED, STARTED, ENDED

### Example Response

```json
[
  {
    "id": 3,
    "name": "TestName",
    "description": "TestDesc",
    "reservedToAffiliates": false,
    "reservedToPartners": false,
    "status": "OPEN",
    "current": false
  }
]

```

## `POST /events`

Create a new event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X POST -d '{"name":"test","description":"test","reserved_to_affiliates":false,"reserved_to_partners":false, "status":"OPEN"}' \
 https://ffs-api.zerator.com/v1/events
```

'status' values: OPEN, CLOSED, STARTED, ENDED

### Example Response

```json
{
	"status": "CREATED",
	"id": 42
}

```

## `GET /event/{EVENT_ID}`

Get an event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X GET \
 https://ffs-api.zerator.com/v1/event/3
```

### Example Response

```json
{
  "id": 3,
  "name": "TestName",
  "description": "TestDesc",
  "reservedToAffiliates": false,
  "reservedToPartners": false,
  "status": "OPEN",
  "current": false,
  "ranking_type": "SCORE_ASC"
}

```

## `PUT /event/{EVENT_ID}`

Update an event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X PUT -d '{"name":"test", "description":"test", "current": false, "reserved_to_affiliates": false, "reserved_to_partners": false, "status": "CLOSED", "ranking_type": "SCORE_ASC"}' \
 https://ffs-api.zerator.com/v1/event/3
```

'status' values: OPEN, CLOSED, STARTED, ENDED

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

## `DELETE /event/{EVENT_ID}`

Delete an event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X DELETE \
 https://ffs-api.zerator.com/v1/event/3
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

## `GET /event/{EVENT_ID}/users`

Get users registered on an event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X DELETE \
 https://ffs-api.zerator.com/v1/event/3/users
```

### Example Response

```json
[
  {
    "twitchId": 74010347,
    "views": 4442,
    "followers": 729,
    "grade": 4000,
    "username": "AlexMogTV",
    "email": "xxxx",
    "url": "https://www.twitch.tv/alexmogtv",
    "broadcasterType": "affiliate"
  }
]
```

## `POST /event/{EVENT_ID}/users`

Register a user on an event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X POST -d '{"twitch_id":1234}' \
 https://ffs-api.zerator.com/v1/event/3/users
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

## `GET /event/{EVENT\\_ID}/user/{USER\\_ID}`

Get registered user's data.

### Example request

```bash
curl -H 'Content-Type: application/json' -X POST -d '{"twitch_id":1234}' \
 https://ffs-api.zerator.com/v1/event/3/user/74010347
```

### Example Response

```json
{
  "twitchId": 74010347,
  "views": 4442,
  "followers": 729,
  "grade": 4000,
  "username": "AlexMogTV",
  "email": "xxxx",
  "url": "https://www.twitch.tv/alexmogtv",
  "broadcasterType": "affiliate",
  "status": "VALIDATED"
}
```

## `PUT /event/{EVENT\\_ID}/user/{USER\\_ID}`

Update registered user's data.

### Example request

```bash
curl -H 'Content-Type: application/json' -X PUT -d '{"status":"REFUSED"}' \
 https://ffs-api.zerator.com/v1/event/3/user/74010347
```

'status' values: VALIDATED, AWAITING_FOR_EMAIL_VALIDATION, AWAITING_FOR_ADMIN_VALIDATION, REFUSED

### Example Response

```json
{
  "code": 200,
  "description": "The request has succeeded",
  "reasonPhrase": "OK",
  "throwable": null,
  "uri": "http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1",
  "error": false,
  "informational": false,
  "globalError": false,
  "success": true,
  "connectorError": false,
  "clientError": false,
  "serverError": false,
  "recoverableError": false,
  "redirection": false
}
```

## `DELETE /event/{EVENT\\_ID}/user/{USER\\_ID}`

Remove registered user.

### Example request

```bash
curl -H 'Content-Type: application/json' -X DELETE \
 https://ffs-api.zerator.com/v1/event/3/user/74010347
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
  "informational": false,
  "globalError": false,
  "success": true,
  "connectorError": false,
  "clientError": false,
  "serverError": false,
  "recoverableError": false,
  "redirection": false
}
```

## `GET /event/{EVENT_ID}/rounds`

Get event rounds.

### Example request

```bash
curl -H 'Content-Type: application/json' -X GET \
 https://ffs-api.zerator.com/v1/event/3/rounds
```

### Example Response

```json
[
	{
		"rounds": "1": [
			"scores": [
			  {
			    "username": "AlexMogTV",
			    "url": "https://www.twitch.tv/alexmogtv",
			    "id": 42,
			    "score": 74010347
			  }
			]
		]
	}
]
```

## `POST /event/{EVENT_ID}/rounds`

Add a new round to the event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X POST \
 https://ffs-api.zerator.com/v1/event/3/rounds
```

### Example Response

```json
{
  "status": "CREATED",
  "id": 2
}
```

## `GET /event/{EVENT\\_ID}/round/{ROUND\\_ID}`

Get round scores from the event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X GET \
 https://ffs-api.zerator.com/v1/event/3/round/2
```

### Example Response

```json
[
  {
    "username": "AlexMogTV",
    "url": "https://www.twitch.tv/alexmogtv",
    "id": 42,
    "score": 74010347
  }
]
```

## `DELETE /event/{EVENT\\_ID}/round/{ROUND\\_ID}`

Removes the round from the event.

### Example request

```bash
curl -H 'Content-Type: application/json' -X DELETE \
 https://ffs-api.zerator.com/v1/event/3/round/2
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
  "informational": false,
  "globalError": false,
  "success": true,
  "connectorError": false,
  "clientError": false,
  "serverError": false,
  "recoverableError": false,
  "redirection": false
}
```

## `PUT /event/{EVENT\\_ID}/round/{ROUND\\_ID}/score/{USER\\_ID}`

Updates the user's score on this round.

### Example request

```bash
curl -H 'Content-Type: application/json' -X PUT -d '{"score":42}' \
 https://ffs-api.zerator.com/v1/event/3/round/1/score/74010347
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
  "informational": false,
  "globalError": false,
  "success": true,
  "connectorError": false,
  "clientError": false,
  "serverError": false,
  "recoverableError": false,
  "redirection": false
}
```