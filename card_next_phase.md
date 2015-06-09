## POST /cards/:id/next_phase.json

Moves the card to the next [phase](phase.md) of the [pipe](pipe.md). 

#### Examples:

```javascript
var ajaxParameters = {
  url: '/cards/1/next_phase.json',
  type: 'PUT'
}
$.ajax(ajaxParameters)
.done(function(data){
  console.log(data);
});
```

