# Miko (巫女)

JavaScript client to make RPC calls to Nameko services.

Inspired by [node-nameko-client](https://github.com/and3rson/node-nameko-client) by [@and3rson](https://github.com/and3rson) 🙏

### Usage

```javascript
const { connect } = require('./index.js');

// First, connect to the queue
// connect returns a promise which will be resolved when everything goes ok
//
//
//  Default options:
//
// host: '127.0.0.1',
// port: 5672,
// login: 'guest',
// password: 'guest',
// exchange: 'nameko-rpc',
// timeout: 5000,
//

connect()
  .then((rpc) => {
    // Use rpc to make calls to nameko services

    rpc
      .fetch('demo_svc', 'noargs')
      // .fetch('demo_svc', 'get_data')
      // .fetch('demo_svc', 'get_data', [2])
      // .fetch('demo_svc', 'get_data', [], { copies: 10})
      // .fetch('demo_svc', 'required_and_optional', ['test'])
      // .fetch('demo_svc', 'variable', ['test', 'another'], { o: 1 })
      // .fetch('demo_svc', 'return_none')
      // .fetch('demo_svc', 'raise_value_error')
      // .fetch('demo_svc', 'raise_exception')
      // .fetch('demo_svc', 'raise_index_error')
        .then((response) => {
          console.log('Response', response);
          rpc.close();
        })
        .catch((err) => {
          console.log('Response error', err);
          rpc.close();
        });
  })
  .catch((err) => {
    console.log('Connection error', err);
  });
```

### License

[MIT](./LICENSE)
