## GET /organizations/:id.json

Gets the JSON representation of a organization in pipefy. Organizations group [pipes]("pipe.md") and [users]("user.md") together.

```json
{
  "id": 1,
  "name": "My Organization",
  "created_at": "2015-01-01T15:54:07.946-03:00",
  "updated_at": "2015-01-01T17:18:21.224-03:00",
"pipes": [
  {
    "id": 1
  },
  {
    "id": 2
  }
]
}
```

##### Relationships:

| attribute | details |
| -- | -- |
| pipes | a list of the organization [pipes](pipe.md). only the pipe `id`'s are listed
```

The other attributes are self explanatory.



