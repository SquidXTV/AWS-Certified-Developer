# [Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)

Elastic Load Balancing automatically distributes your incoming traffic across multiple targets, such as EC2 instances, containers, and IP addresses,
in one or more Availability Zones. It monitors the health of its registered targets, and routes traffic only to the healthy targets.
Elastic Load Balancing scales your load balancer capacity automatically in response to changes in incoming traffic.

## [ELB Target Groups](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)

Target groups route requests to individual registered targets, such as EC2 instances, using the protocol and port number that you specify.
You can register a target with multiple target groups. You can configure health checks on a per target group basis. Health checks are performed
on all targets registered to a target group that is specified in a listener rule for your load balancer.

### [ELB Target Groups Target Type](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html#target-type)

When you create a target group, you specify its target type, which determines the type of target you specify when registering targets with this target group.
After you create a target group, you can't change its target type.

- instance
- ip (private ip only)
- lambda



## [ELB Cross-Zone Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html#availability-zones)

When you enable an Availability Zone for your load balancer, Elastic Load Balancing creates a load balancer node in the Availability Zone.
If you register targets in an Availability Zone but do not enable the Availability Zone, these registered targets do not receive traffic.

The nodes for your load balancer distribute requests from clients to registered targets. When cross-zone load balancing is enabled,
each load balancer node distributes traffic across the registered targets in all enabled Availability Zones. When cross-zone load balancing is disabled,
each load balancer node distributes traffic only across the registered targets in its Availability Zone.


## [ELB HTTP Headers](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html#request-routing)

Application Load Balancers and Classic Load Balancers automatically add `X-Forwarded-For`, `X-Forwarded-Proto`, and `X-Forwarded-Port` headers to the request.


## [ELB Load Balancer Types](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html#elb-features)

### [Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)

An Application Load Balancer functions at the application layer, the seventh layer of the Open Systems Interconnection (OSI) model.
After the load balancer receives a request, it evaluates the listener rules in priority order to determine which rule to apply,
and then selects a target from the target group for the rule action. You can configure listener rules to route requests to different
target groups based on the content of the application traffic such as headers, request method, path patterns, and query strings.


### [Network Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html)

A Network Load Balancer functions at the fourth layer of the Open Systems Interconnection (OSI) model. It can handle millions of requests per second.
After the load balancer receives a request from a client, it selects a target from a target group in the default action.
It attempts to send the request to the selected target using the protocol and port that you specified.



## [ELB Sticky Sessions](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/edit-target-group-attributes.html#sticky-sessions)

By default, an Application Load Balancer routes each request independently to a registered target based on the chosen load-balancing algorithm.
However, you can use the sticky session feature (also known as session affinity) to enable the load balancer to bind a user's session to a specific target.
This ensures that all requests from the user during the session are sent to the same target.
This feature is useful for servers that maintain state information in order to provide a continuous experience to clients.
To use sticky sessions, the client must support cookies.

