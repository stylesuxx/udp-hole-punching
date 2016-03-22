# UDP hole punching
> UDP hole punching server and client implementation with twisted in python.

## Prerequisites
All systems where either *client* or *server* are running need to have python 2.7 installed.
Further the [twisted networking engine](https://twistedmatrix.com) is required.

## Running
The server needs to run on a system with a public reachable IP.

The clients need to run on two separate hosts behind (at least one) NAT, like for example a home router.

### Server
The server is used by the clients to exchange connection details. The public IP address and port of the server is known by both clients.
```
Usage: ./server.py PORT
```

### Client
Clients connect to the rendezvous server and wait for connection details about another peer to be transmitted by the server.
Once this is done, they initialize a connection with each other and start exchanging messages.
```
Usage: ./client.py RENDEZVOUS_IP RENDEZVOUS_PORT
```

## Sample output
After starting the server and both clients you should see the following output
when hole punching worked between the two peers:

**Server:**
```
Listening on *:9999
Registration from xxx.109.xxx.90:43242
Registration from 184.xxx.19.xxx:59019
Linked peers
```

**Client A:**
```
Connected to server, waiting for peer...
Sent init to 184.xxx.19.xxx:59019
Received: Message from 0.0.0.0:59019
```

**Client B:**
```
Connected to server, waiting for peer...
Sent init to 80.109.103.90:43242
Received: Message from 0.0.0.0:43242
```

## References
[Peer-to-Peer Communication Across Network Address Translators](http://www.brynosaurus.com/pub/net/p2pnat/)
