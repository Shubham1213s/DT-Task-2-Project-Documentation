#Task 2 – API Documentation

Feature: Nudge Creation for Events / Articles

A Nudge is a scheduled notification or prompt created by a user to highlight an event or article.
It includes a title, description, image, schedule time, icon, and a one-line invitation message.
Nudges can be previewed, published immediately, or scheduled for later.

Nudge Object Data Model 

{
  "type": "nudge",
  "uid": 18,
  "target_type": "event",
  "target_id": "65ab123...",
  "title": "Workshop Reminder",
  "image": "image_url",
  "schedule_date": "2026-01-03",
  "time_from": "11:00",
  "time_to": "02:00",
  "description": "A short description explaining the purpose of the nudge",
  "icon": "xyz",
  "invitation_text": "There’s a great workshop coming up. Swipe to check it out.",
  "status": "scheduled",
  "created_at": "2026-01-03T11:00:00Z"
}

Field Description

type - Identifies the object as a nudge
uid - User ID who created the nudge
target_type - Event or Article
target_id - Unique ID of the tagged event/article
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


Base URL - /api/v3/app

CRUD API Documentation for Nudge

1. Create a Nudge

Request Type: POST
Endpoint: /nudges

Payload:
{
  "uid": 18,
  "target_type": "event",
  "target_id": "65ab123...",
  "title": "Reflection Workshop Reminder",
  "image": "image_url",
  "schedule_date": "2026-01-10",
  "time_from": "10:00",
  "time_to": "11:00",
  "description": "Reminder for reflection workshop",
  "icon": "bell",
  "invitation_text": "There’s a great workshop coming up. Swipe to check it out."
}



Creates a new nudge for an event or article and returns the nudge ID.
