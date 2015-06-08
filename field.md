## GET /fields/:id.json

Gets the JSON representation of a [phase]("phase.md") field.

This is the **structure** of a field in pipefy. The **values** of fields have their own entity: [Field Values]("field_value.md").

##### Main data of the phase:

```json
{
  "id": 1,
  "phase_id": 1,
  "label": "My field",
  "default_value": null,
  "type_id": 1,
  "index": 1.0,
  "options": [],
  "created_at": "2015-01-01T15:42:27.341-03:00",
  "updated_at": "2015-01-01T15:42:27.341-03:00"
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
| type_id | the [field type](field_type.md) of the field (to be documented). |
| phase_id | id of the [phase]("phase.md") the field belongs. |
