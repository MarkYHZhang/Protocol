# Protocol V1
A repo just for the protocol XD

## Type 1 packets

Each packet consists of a list of `action`s, which represent an action that an entity performs. For example:
 - Bot accelerating
 - Bullet moving
 - Bot aiming
 
Packets sent from client to server consist of an action that the client wants to perform, which is then verified by the server, and then updated in global state. An example is the client `fire`s a bullet from one of their bots.

Every server step, a packet is sent to each client consisting of a list of `action`s that entities within view have performed. Each `action` contains the actual action that the client performed, as well as the current authoritative (server verified) state of the client.

Example of transaction between client and server:

 1. Client sends `move` action to server, containing the requested x and y acceleration
 2. Server verifies and simulates movement of client in 1 server step/tick
 3. Server broadcasts `move` action to all clients in range, containing the x and y position and velocity of the client which moved

Example in JSON:
```json
//sync packet sent from client to server
{
	playerUUID: "eoiroieut",
	actions:
	[
		{
			action: "movement",
			params: {
				botUUID: "cust",
				yAccel: 100,
				xAccel: 10
			}
		}
	]
}

//sync packet sent from server to clients
{
	actions:
	[
		{
			action: "movement",
			params: {
				entityUUID: "cust",
        			entityType: "bot"
				yVel: 100,
				xVel: 10,
				x: -100,
				y: 200
			}
		}
	]
}
```
