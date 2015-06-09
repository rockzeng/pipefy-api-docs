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
