# Node.js Classes

## `req`: IncomingMessage
[Full documentation](https://nodejs.org/api/http.html#class-httpincomingmessage) for `IncomingMessage`

Notable built-in properties
```ts
headers: object
method:  string
url:     string
```
Properties added by Spinneret
```ts
body:    object || Buffer // object if JSON, otherwise Buffer
cookies: object           // object of cookies from the Cookie header
params:  object           // object of URL parameters after the question mark ?
vars:    object           // object of URL variables in the path
```

## `res`: ServerResponse
[Full documentation](https://nodejs.org/api/http.html#class-httpserverresponse) for `node.http.ServerResponse`

The way to respond to the client after processing the request. Call `end`

Notable built-in properties/functions
```ts
end:        function(data = null)
setHeader:  function(name, value)
finished:   boolean
statusCode: number
```

Parameters of above functions
```ts
data:  string || Buffer || Uint8Array
name:  string
value: any
```

Functions added by Spinneret middleware `server.midApiResEnd`
```ts
endJson:          function(obj)
endBadRequest:    function()
endUnauthorized:  function()
endNotFound:      function()
endInternalError: function()
```

Parameters of above functions
```ts
obj: object
```

## `soc`:  Socket
[Full documentation](https://nodejs.org/api/net.html#class-netsocket) for `node.net.Socket`

The WebSocket of the client. The `message` property is a full message as a Buffer. As opposed to an HTTP body, the type is unknown, so you must manually call JSON.parse on the message if it is JSON.

Functions added by Spinneret
```ts
encode: function(data)
send:   function(data, encoded=false)
```

Properties added by Spinneret
```ts
error:    Exception || null // non-null if the event-handler is 'error'
hadError: boolean || null   // non-null if the event-handler is 'close'
message:  Buffer || null    // non-null if the event-handler is 'data'
```

Parameters of functions above
```ts
data:    Buffer || object
encoded: boolean
```
