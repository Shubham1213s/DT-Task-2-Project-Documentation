## Task 2 – API Documentation

# Feature: Nudge Creation for Events / Articles

A Nudge is a scheduled notification or prompt created by a user to highlight an event or article.
It includes a title, description, image, schedule time, icon, and a one-line invitation message.
Nudges can be previewed, published immediately, or scheduled for later.

## Nudge Object Data Model 

```json
{
  "type": "nudge",
  "uid": 18,
  "target_type": "event",
  "target_id": "65ab123...",
  "title": "Live Class Alert",
  "image": "image_url",
  "schedule_date": "2026-01-03",
  "time_from": "10:00",
  "time_to": "11:00",
  "description": "A short description that explains the purpose of the nudge",
  "icon": "icon_image",
  "invitation_text": "An interesting class is there. Please Watch Live Class",
  "status": "scheduled",
  "created_at": "2026-01-04T11:00:00Z"
}
```
## Field Description

type - It identifies the object as a nudge
uid - User ID who created the nudge
target_type - Event or Article
target_id - Unique ID of the tagged event
title - Nudge title (max 60 characters)
image - image for the nudge
schedule_date - Date on which nudge should be sent
time_from - Start time
time_to	- End time
description - Detailed nudge description
icon - Icon shown when nudge is minimized
invitation_text	- One-line invitation message
status - draft / scheduled / published
created_at - Creation timestamp


## Base URL - /api/v3/app

## CRUD API Documentation for Nudge

1. Creation of a Nudge

Request Type: POST
Endpoint: /nudges

Payload:
```json
{
  "uid": 18,
  "target_type": "event",
  "target_id": "1234...",
  "title": "Trading Live Class Alert",
  "image": "image_url",
  "schedule_date": "2026-01-03",
  "time_from": "10:00",
  "time_to": "11:00",
  "description": "Reminder for Live class",
  "icon": "bell",
  "invitation_text": "An interesting class is there. Please Watch Live Class"
}
```
Info/Description - Creation of a new nudge for an event and return the nudge ID.

2. Get Nudge by ID

Request Type: GET
Endpoint: /nudges?id=:nudge_id

Payload: None

Info/Description: It fetches a nudge using its unique ID.

3. Get All Nudges (Pagination Requirement)

Request Type: GET
Endpoint: /nudges?limit=10&page=1


Payload: None

Info/Description: It will return a paginated list of nudges created by users.

4. Update a Nudge

Request Type: PUT
Endpoint: /nudges/:id


Payload:
```json
{
  "title": "Updated Nudge Title",
  "description": "Updated description",
  "schedule_date": "2026-01-12"
}
```

Info/Description: It updates fields of an existing nudge.

5. Delete a Nudge

Request Type: DELETE
Endpoint: /nudges/:id


Payload: None

Info/Description: It deletes a nudge using its unique ID.


## Functional Observations

 -  While creating a nudge, User can able to tag an event

 - Image uploaded during this will be used as cover image

 - when the nudge is triggered then Time and date will define
 
 - When nudge is minimized or embedded then Icon and invitation text will display
 
 - Preview functionality uses the same payload without it publishing

 - MongoDB `_id` used as unique identifier
   
 - No fixed schema is there. It shows flexibility.

## Final Conclusion
Basically, this API design enables users to create, schedule, manage, and display nudges associated with events or articles. It follows a clear CRUD-based structure and aligns with the provided wireframe and functional requirements.
