## PUT /cards/:id/previous_phase.json

Moves the card to the previous [phase](phase.md) of the [pipe](pipe.md). 

#### Examples:

```javascript
var ajaxParameters = {
  url: '/cards/1/previous_phase.json',
  type: 'PUT'
};
$.ajax(ajaxParameters)
.done(function(data){
  console.log(data);
});
```

