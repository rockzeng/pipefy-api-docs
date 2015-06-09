## GET /card_field_value/:id.json

Gets the JSON representation of a card [field]("field.md") value (mainly user's input).

```json
{
  "id": 1,
  "field_id": 1,
  "value": "Warner",
  "display_value": "Warner",
  "created_at": "2015-01-01T15:54:10.737-03:00",
  "updated_at": "2015-01-01T15:54:10.737-03:00",
  "card": {}
}
```
##### Attributes:

(to be documented)

##### Relationships:

| attribute | details |
| -- | -- |
| field_id | id of the [field]("field.md") this card field value belongs to. |
| card | a small representation of the [card](card.md) of the field value (included for convenience). |

#### Examples:

##### To list all the field values of the current phase of a card:

```javascript
$.get('/cards/1.json', function(card, status){
  $.each(card.current_phase_detail.field_values, function(index, field_value){
    console.log(field_value.value);  
  })
});
```

##### To list all the fields of the current phase of the card, with its respective values:
```javascript
$.get('/cards/1.json', function(card, status){

  $.each(card.current_phase_detail.phase.fields, function(index, field){
    
    // Finds field values by field_id:
    var field_value = $.map(card.current_phase_detail.field_values, function(field_value){
      if (field_value.field_id === field.id) return field_value;
    });
    
    // As field values exist only after they are set (created), set a default value if they are missing:
    if (field_value[0]) { 
      field_value = field_value[0].value;
    } else { 
      field_value = '<no value yet>'; 
    };
    
    console.log("field id: " + field.id + "; field label: '" + field.label + "'; field value: '" + field_value + "'");
  })
  
});
```

##### To set a "field value" value:

You need to POST to the `card_field_values` endpoint with the `card_phase_detail_id` and the `field_id`:

```javascript
var fieldValueObject = {"card_field_value": {"field_id": 1, "value": "Foo", "card_phase_detail_id": 1}};
$.post('/card_field_values.json', fieldValueObject, function(data){
  console.log(data);
});
```
