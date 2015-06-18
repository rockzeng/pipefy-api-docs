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

In order to create a new card setting values for fields, you must remember:

The card is **created** on the first, **draft** phase of the pipe, then automatically **moved** to the next **non draft** phase. So, the fields getting values set are **from the first, draft** phase.

You need to specify which fields are getting values set, by their ids. If you're starting knowing only the pipe id, you need to:
  1. Get the first [phase](phase.md) id from the list of the pipe phases;
  2. With the phase id you neet to get all the [field](field_.md) ids of that phase;
  3. Finally, you send the [field values](field_value.md) (only `field_id` and `value` are needed) associated to field ids.

```javascript
var pipeId = 1;
var firstPhase, fieldIds;

var fieldValues = [
  { "field_id": 1, "value": "value for first field (which also can be used as the card title)" },
  { "field_id": 2, "value": "value for second field" },
  { "field_id": 3, "value": ["value for a radio (yes/no) field"] },
  { "field_id": 4, "value": ["multiple values", "for a ", "checklist field"] }
];

var cardObject = {
  "card": {
    "field_values": fieldValues
  }
};

$.post('/pipes/' + pipeId + '/create_card.json', cardObject, function(data){
  console.log(data);
});
```

Here is a full example, doing it all at once:

```javascript

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
    var fieldValuesArray = $.map(fieldIds, function(fieldId){
      if (fieldId === 1) return {field_id: fieldId, value: 'value for first field'};
      if (fieldId === 2) return {field_id: fieldId, value: 'value for second field'};
    });
    // finally, create a new card with some field values
    var cardObject = {"card": {"title": "My new card", field_values: fieldValuesArray}};
    $.post('/pipes/' + pipeId + '/create_card.json', cardObject, function(data){
      console.log(data);
    });
  });
});
```