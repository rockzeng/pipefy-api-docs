## GET /pipes/:id.json

Gets the JSON representation of the Pipe as a whole, including nested resources. 

This is one of the most complete server responses of pipefy. The resulting
JSON contains data from the Pipe itself and much data from its children
relationships, like [users](user.md), [labels](label.md) and [phases](phase.md):

##### Main data of the pipe:

```json
{
  "id": 1,
  "name": "My Pipe",
  "created_at": "2015-01-01T21:45:51.300-03:00",
  "updated_at": "2015-02-07T08:42:29.756-03:00",
  "token": "802ed724e6cca1b384157cbe17102ef558ca65c1",
  "can_edit": true,
  "labels": [],
  "users": [],
  "phases": []
}
```
##### Labels of the pipe:

```json
"labels": [
    {
      "id": 1,
      "name": "Bug",
      "color": "#E64A4A"
    },
    {
      "id": 2,
      "name": "New feature",
      "color": "#A24ED9"
    }
]
```

##### Users (members of the pipe):
```json
"users": [
  {
    "id": 1,
    "name": "John Doe",
    "username": "johndoe",
    "email": "johndoe@mail.com",
    "display_username": "johndoe"
  },
  {
    "id": 2,
    "name": "Jane Doe",
    "username": "",
    "email": "jane.doe@mail.com",
    "display_username": "jane.doe"
  }
]
```

##### Phases of the pipe:

Here is a example of two phases, each one containing two cards each.

```json
"phases": [
  {
    "id": 1,
    "name": "First Phase",
    "description": "First phase of the pipe!",
    "done": false,
    "pipe_id": 1,
    "index": 0.0,
    "draft": true,
    "cards": [
      {
        "id": 1,
        "title": "First card",
        "current_phase_id": 1,
        "due_date": null,
        "index": null
      },
      {
        "id": 2,
        "title": "Second card",
        "current_phase_id": 1,
        "due_date": null,
        "index": null
      }
    ]
  },
  {
    "id": 2,
    "name": "Second Phase",
    "description": "Second phase of the pipe!",
    "done": false,
    "pipe_id": 1,
    "index": 1.125,
    "draft": false,
    "cards": [
      {
        "id": 3,
        "title": "First card on the second phase",
        "current_phase_id": 2,
        "due_date": null,
        "index": -59.0
      },
      {
        "id": 4,
        "title": "Second card on the second phase",
        "current_phase_id": 2,
        "due_date": null,
        "index": -58.0
      }
    ]
  }
]
```

### Example usage

To get the pipe name:

```javascript
$.get('/pipes/1.json', function(pipe, status){
  console.log(pipe.name);
});
```

To get the name of all the phases of a pipe:

```javascript
$.get('/pipes/1.json', function(pipe, status){
  $.each(pipe.phases, function(index, phase){
    console.log(phase.name);  
  })
});
```

To get the card titles of all cards in the first phase of a pipe:

```javascript
$.get('/pipes/1.json', function(pipe, status){
  $.each(pipe.phases[0].cards, function(index, card){
    console.log(card.title);  
  })
});
```