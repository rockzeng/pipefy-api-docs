## GET /pipes/:id.json

Gets the JSON representation of the Pipe as a whole
(including nested resources).

### Example usage

To get the pipe name:

```
$.get('/pipes/1.json', function(data, status){
  console.log(data.name);
});
```


This is one of the most complete server responses of pipefy. The resulting
JSON contains data from the Pipe itself and much data from its children
relationships:

##### Labels:

```
"labels": [
    {
      "id": 1,
      "name": "Bug",
      "color": "#E64A4A"
    },
    {
      "id": 2,
      "name": "New feature",
      "color": "#A24ED9"
    }
]
```


To get the name of the first label of the Pipe:

```
$.get('/pipes/1.json', function(data, status){
  console.log(data.labels[0].name);
});
```

##### Users (members of the pipe):
```
"users": [
  {
    "id": 1,
    "name": "John Doe",
    "username": "johndoe",
    "email": "johndoe@mail.com",
    "display_username": "johndoe"
  },
  {
    "id": 2,
    "name": "Jane Doe",
    "username": "",
    "email": "jane.doe@mail.com",
    "display_username": "jane.doe"
  }
]
```