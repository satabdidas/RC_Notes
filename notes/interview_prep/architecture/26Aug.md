Architectural Whiteboarding

Discussion A
============
1 Load-balancer
2 web servers

A developer was making changes, building the code and manually, testing it and deploying on the 2 web-servers.

Design a server that does that automatically.

deploy server -> post request (why? why not ssh or rsync?)

Things to think of
- Downtime - may be take one server off the load-balancer, update that, and then put it back into the pool again.
- different versions of the website due to time diff in deployment
- what if 2 developers push request for deploying
  - some sort of blocking mechanism
- What if the application gets more complicated, more servers are being added. For instance pdf server, cache etc.
- How to display status of the deployment
- How to revert back

Discussion B
============

A media storage

Write
- Key/Name (foo)
- Type (mp3, jpeg)
- Data

Read
- Key
- Type

Question: If there's a LB in between, when a request comes,
