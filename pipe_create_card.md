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
var pipeId = 1;
var firstPhase, fieldIds;
// get pipe details, phases details included
$.get('/pipes/' + pipeId + '.json', function(pipe, status){
  // get the first phase of the pipe
  firstPhase = pipe.phases[0];
})
.success(function(data){
  // get the fields of the first phase of the pipe
  $.get('/phases/' + firstPhase.id + '.json', function(phase, status){
    // get the field ids
    fields = phase.fields;
    fieldIds = $.map(fields, function(field){
      return field.id;
    });
  })
  .success(function(data){
    // make a list of field value objects:
    fieldValuesArray = $.map(fieldIds, function(fieldId){
      if (fieldId === 1) return {field_id: fieldId, value: 'value for first field'};
      if (fieldId === 2) return {field_id: fieldId, value: 'value for second field'};
    });
    // finally, create a new card with some fiel values
    var cardObject = {"card": {"title": "My new card", field_values: fieldValuesArray}};
    $.post('/pipes/' + pipeId + '/create_card.json', cardObject, function(data){
      console.log(data);
    });
  });
});
```