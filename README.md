# Protocol
A repo just for the protocol XD

Current ideas:
```json
{
	playerUUID: "eoiroieut",
	actions: <-- support multiple actions in one "packet"
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

//response packet
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
				currX: -100,
				currY: 200
			}
		},
		{
			action: "movement",
			params: {
				entityUUID: "wretre",
        entityType: "bullet"
				yVel: 100,
				xVel: 10,
				currX: -100,
				currY: 200
			}
		}
	]
}
```
