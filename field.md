## GET /fields/:id.json

Gets the JSON representation of a [phase]("phase.md") field. Includes its fields, jump targets (other phases where a card can be moved to) and connected cards (other cards that can be connected to the card through the phase).

##### Main data of the phase:

```json
{
  "id": 1,
  "name": "My Phase",
  "pipe_id": 1,
  "index": 0.0,
  "created_at": "2015-01-01T15:42:26.974-03:00",
  "updated_at": "2015-01-01T15:42:26.974-03:00",
  "can_edit": true,
  "fields": [],
  "connected_pipes": [],
  "jump_targets": []
}
```

| attribute | details |
| -- | -- |
| index | the position (order) where the phase is listed on the [pipe]("pipe.md"). |

##### Relationships:

| attribute | details |
| -- | -- |
| pipe_id | the [pipe](pipe.md) of the phase. |
| fields | the list of [fields]("field.md") of the phase. |
| connected_pipes | the list of connected [pipes](pipe.md) of the phase. |
| jump_targets | optional list of phases (other than "previous" and "next" ones) where cards on this phase can be moved to |

