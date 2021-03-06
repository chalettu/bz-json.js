# bz-json.js

A JavaScript wrapper for the [Bugzilla JSON-RPC API](http://www.bugzilla.org/docs/tip/en/html/api/Bugzilla/WebService/Server/JSONRPC.html).

# install
For [node](http://nodejs.org) install with [npm](http://npmjs.org):

```	
npm install bz-json
```

and use with `var bz = require("bz-json")`

For the browser, build a browser file from the source code with [browserbuild](https://github.com/LearnBoost/browserbuild): `browserbuild bz-json.js`.

# usage

```javascript
var bugzilla = bz.createClient();

bugzilla.getBug(678223, function(error, bug) {
  if (!error) {
    alert(bug.summary);
  }
});
```

# API
`bz.createClient(options)`
creates a new Bugzilla API client, optionally takes options like the JSON-RPC API url and username + password:

```javascript
var bugzilla = bz.createClient({
  url: "https://bugzilla.mozilla.org/jsonrpc.cgi",
  username: 'bugs@bugmail.com',
  password: 'secret'
});
```

### Client methods
Each method takes a callback that takes an error message (if any kind of error occurs) as its first argument, and the expected return data as its second.

`getBug(id, callback)`  
retrieves a [bug](http://www.bugzilla.org/docs/tip/en/html/api/Bugzilla/WebService/Bug.html) given a bug id.

