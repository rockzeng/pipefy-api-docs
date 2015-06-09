## POST /cards.json

Creates a new card on a [pipe](pipe.md). The body of the JSON document tells which card, in which phase the comment is created.

```json
{
  "comment": {
    "text": "My awesome comment", 
    "card_phase_detail_id": 1
  }
}
```
The currently authenticated user will be automatically set as the comment creator.

#### Examples:

##### To create a new comment on a card:

```javascript
var commentObject = {"comment": {"text": "My awesome comment", "card_phase_detail_id": 1}};
$.post('/comments.json', commentObject, function(data){
  console.log(data);
});
```

The same operation, treating error responses:

```javascript
var commentObject = {"comment": {"text": "My awesome comment", "card_phase_detail_id": 1}};
$.post('/comments.json', commentObject)
  .success(function(data){
    console.log(data.id);
  })
  .error(function(data){
    console.log(data.status);
  });
```







-------------------

Gets the JSON representation of a Card. 

The resulting JSON contains **all** the data from the card itself and much data from its children relationships, like [assignees](user.md), [labels](label.md) and previous/current/next [phases](phase.md):

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
  "assignees": [],
  "labels": [],
  "current_phase_detail": {},
  "other_phase_details": [],
  "checklists": []
}
```
##### Attributes:

| attribute | details |
| -- | -- |
| id | id of the card. |
| title | title of the card. |
| duration | duration (diff from `started_at` to current time) of the card in seconds |
| current_phase_id | id of the current phase of the card. |
| due_date | due date of the card. |
| started at | the moment when the card left the launchpad. |
| finished_at | the moment when the card was first moved to a "done phase". |
| expiration_time | the moment the card will be marked as expired. |
| index | the index (position) of the card on the current phase.  |
| token | unique token used for integrations. |
| expired | flag to mark the card as expired. |
| late | flag to mark the card as late. |
| draft | flag to mark if the card is a draft (still on the launchpad). |
| done | flag to mark if the card has passed to a "done phase". |
| checklists | custom checklists created on the card. |

The remaining of the attributes are self explanatory.

##### Relationships:

| attribute | details |
| -- | -- |
| pipe | small representation of the [pipe]("pipe.md") of the card, including its `id` and `name`. |
| previous_phase | small representation of the [phase]("phase.md") the card can return to. |
| next_phase | small representation of the [phase]("phase.md") the card can go next. |
| assignees | list of [users]("user.md") assigned to card. |
| labels | list of the [labels]("label.md") of the card. |
| current_phase_detail | the current phase details of the card, including fields and values. |
| other_phase_detailS | list of other (previous or next) phase details of the card, including its fields and (possible) values. |


