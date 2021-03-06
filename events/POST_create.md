# Create Event

    POST services/:service_id/events
    
Create an event. The response depends on the type of event being created:
*When creating (sending) a message* returns an array of Message IDs queued for sending.
*When creating a note* returns the created note event

### User Authorization Classes 
* account
* contact (requires x-zingle-contact-id header)

## Parameters
### URI Parameters
None

### JSON Body Parameters
#### Creating a message
See the [Create Message] call

#### Creating a note
Field | Data Type | Required | Description
--- | --- | --- | ---
event_type | string | Y | The type of event - for notes must be 'note'
contact_id | string | Y | The ID of the contact whose conversation the note should be created on
body | string | Y | The note body
template_id | string | N | The ID of the template of which the event should include

## Example
### Request

    POST https://api.zingle.me/v1/services/1d06e84f-8152-4de7-983d-a2d88b73734a/events
#### Request Body
```json
{
    "event_type": "note",
    "contact_id": "1d06e84f-8152-4de7-983d-a2d88b73734a",
    "body": "This guest is very thoughtful",
    "template_id": "9673c6cf-d5a7-4df6-bf9f-9c7f569f9de1"
}
```

### Response
``` json
{
  "status": {
    "text": "OK",
    "status_code": 200,
    "description": null
  },
  "result": {
    "id": "1d42c7f9-6cc0-48eb-8fe1-db059c466c4e",
    "contact_id": "1a2bca74-19e1-4440-b025-74b5c18a20d2",
    "event_type": "note",
    "body": "This guest is very thoughtful",
    "created_at": 1442249007,
    "triggered_by_user": {},
    "automation": {},
    "message": {}
  }
}
```

[Create Message]: /messages/POST_create.md
