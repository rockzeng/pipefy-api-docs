## GET /fields/:id.json

Gets the JSON representation of a [card]("card.md") (technically, a [card phase detail]("card_phase_detail.md")) comment.

```json
{
  "id": 86,
  "text": "My very constructive comment!",
  "created_at": "2015-06-08T17:50:56.555-03:00",
  "updated_at": "2015-06-08T17:50:56.555-03:00",
  "card_phase_detail_id": 152,
  "created_by": {}
}
```
##### Attributes:

The attributes are self explanatory.

##### Relationships:

| attribute | details |
| -- | -- |
|card_phase_detail_id| the id of the [card phase detail]("card_phase_detail.md") which the comment was created.|
| created_by | a representation of the [user]("user.md") who created the comment. |

#### Examples:

##### To list all the comments of a card:

```javascript
$.get('/cards/1.json', function(card, status){
  $.each(card.comments, function(index, comment){
    console.log(comment.text);  
  })
});
```

##### To create a new comment on a card:


