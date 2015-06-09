## POST /pipes/:id/create_card.json

Creates a new card on the first non draft phase of a [pipe](pipe.md). 

```json
{
  "card": {
    "title": "My new card"
  }
}
```
The currently authenticated user will be automatically set as the card creator.

#### Examples:

##### To create a new comment on a card:

```javascript
var cardObject = {"card": {"title": "My new card"}};
$.post('/pipes/2/create_card.json', cardObject, function(data){
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