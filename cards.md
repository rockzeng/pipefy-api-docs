## GET /cards/:id.json

Gets the JSON representation of a Card. 

The resulting JSON contains **all** the data from the Card itself and much data from its children relationships, like assignees, labels and previous/current/next phases:

##### Main data of the card:

```json
{
  "id": 1,
  "title": "My card",
  "current_phase_id": 2,
  "due_date": null,
  "duration": 346529.265369079,
  "started_at": "2015-01-01T10:02:53.708-03:00",
  "finished_at": null,
  "expiration_time": "2015-01-21T10:02:53.708-03:00",
  "index": -15.0,
  "token": "09b5a26f81bdffb46ac595a25af857ecc669448b",
  "pipe": {
    "id": 1,
    "name": "My pipe"
  },
  "expired": false,
  "late": true,
  "draft": false,
  "done": false,
  "can_show_pipe": true,
  "previous_phase": {
    "id": 1,
    "name": "First phase",
    "draft": true
  },
  "next_phase": {
    "id": 3,
    "name": "Third phase"
  },
  "assignees": [...],
  "labels": [...],
  "current_phase_detail": {},
  "other_phase_details": [...],
  "checklists": [...]
}
```

| attribute | details |
| -- | -- |
| id | id of the card. |
| title | title of the card. |
| duration | duration (diff from `started-at` to current time) of the card in seconds |
| current_phase_id | id of the current phase of th card. |
| due_date | due date of the card. |
| started at | the moment when the card left the launchpad. |
| finished_at | the moment when the card was first moved to a "done phase". |
| expiration_time | the moment the card will be marked as expired. |
| index | the index (position) of the card on the current phase.  |
| token | unique token used for integrations. |
| pipe | small representation of the pipe of the card, including its `id` and `name`. |
| expired | flag to mark the card as expired. |
| late | flag to mark the card as late. |
| done | flag to mark if the card has passed to a "done phase". |
|  |  |
|  |  |
