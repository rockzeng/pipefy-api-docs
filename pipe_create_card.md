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

##### To create a new card on the first non draft phase of a pipe, setting the card title:

```javascript
var cardObject = {"card": {"title": "My new card"}};
$.post('/pipes/1/create_card.json', cardObject, function(data){
  console.log(data);
});
```

##### To create a new card on the first non draft phase of a pipe, setting more field values:

1. Get the field `id`s of the phase. The phase can be the first, draft phase.;
2. Set the field values for each field;

```javascript
var firstPhase;
// get pipe details, phases details included
$.get('/pipes/2.json', function(pipe, status){
  // get the first phase of the pipe
  firstPhase = pipe.phases[0];
})
.success(function(data){
  // get the fields of the first phase of the pipe
  console.log(firstPhase.id)
});
```