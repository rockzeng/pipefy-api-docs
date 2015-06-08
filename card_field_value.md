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

| attribute | details |
| -- | -- |
| index | the position (order) where the field is listed on the [phase]("phase.md"). |
| options | (to be documented) |

The remaining of the attributes are self explanatory.

##### Relationships:

| attribute | details |
| -- | -- |
| field_id | id of the [field]("field.md") this card field value belongs to. |
| card | a small representation of the [card](card.md) of the field value (included for convenience). |

