# Miko (巫女)

At Sohonet, we embrace microservices. They allow us to move faster, scale up easily and experiment with different technologies. One problem you need to solve with microservices architecture is the communication between services. You can use RESTful API, RPC calls or any other method to send data across services.

Since we are using Python in our backend services, we use Nameko. Nameko is a microservices framework for Python that lets service developers concentrate on application logic. You can have many separate Python services that can talk to each other and feel like a one big system.

Under the hood, Nameko is using messaging queues to send requests and share data across services.

It all works nice as long as you are in the Python realm. But what if you need to share data across Python and Javascript services?

Enter Miko.

Miko is a Javascript library for communicating with Nameko services. It connects to the same queue Nameko uses and can send requests to Nameko services written in Python. Python services then respond to the request and send back the response to Javascript service.

With Miko, we can let backend and frontend developers do what they do the best. Frontend developers can focus on services that serve the frontend, while backend developers can focus on optimizing backend services, letting everyone move faster. Win-win for everyone!

Let's see Miko in action then, shall we?

I assume you have your Nameko services up and running.

Install Miko by typing `npm install miko`.

Talking to Nameko with Miko is very easy. Just connect to the queue, make the request, grab the response and it's done!

Here is the above sentence written in Javascript:

```javascript
import { connect } from 'miko';

// First, connect to the queue
// connect returns a promise which will be resolved when everything goes ok
//
//
// Default options:
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
      .fetch('nameko_service', 'get_pizza')
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

And that's it. Now you are ready to call Python methods via Nameko in Javascript.

You can check Miko's code here: https://github.com/sohonetlabs/miko

Miko brings together two worlds - Python and Javascript. This is reflected in the name of the library. Miko (巫女) is a Japanese name of a female shaman who knows how to connect earth to the heavens.
