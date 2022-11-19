# Load Balancer
> Much more traffic from the users must be handled , the resource that you use get overloaded from the bunch of requests on that resource, so you decide to make one more copy of that resource to handle more requests, but how can you manage the requests to load on 2 resources?

- Adding a load balancer in front of these copies of resources to handle the traffic, so now we can handle where traffic goes.

> Load Balancer distributes new _inbound flows_ that arrives to the load balancer's frontend to backend pool instances, according to rules and health propes.

- inbound flows => Traffic from internet or local network
- frontend Load Balancer => The access point for Load Balancer, all traffic goes here first
- backend pool => resources that process requests
- rules and health propes => Checks to ensure backend instances can retrieve the data

## Scenarios
- Intrernet traffic : balance the internet requests traffic
- Internal Network: A load balancer works well with internal apps
- Port forwarding : Traffic can be forwarded to a specific machine and specific app
- Outbound traffic: Allow outbound connectivity for backend pools