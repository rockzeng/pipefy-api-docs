## GET /cards/:pipe_id/:card_id.json

Gets the JSON representation of a Card belonging to a Pipe. 

This is one of the most complete server responses of pipefy. The resulting
JSON contains data from the Pipe itself and much data from its children
relationships, like users, labels and phases:

##### Main data of the pipe: