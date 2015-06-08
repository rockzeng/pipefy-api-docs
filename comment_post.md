## POST /comments.json

Creates a nes comment. The body of the JSON document tells which card, in which phase the comment is created.

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

