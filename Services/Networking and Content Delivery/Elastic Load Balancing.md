# [Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)

## [ECS Load Balancing Target Groups](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)

Target groups route requests to individual registered targets, such as EC2 instances, using the protocol and port number that you specify.
You can register a target with multiple target groups. You can configure health checks on a per target group basis. Health checks are performed
on all targets registered to a target group that is specified in a listener rule for your load balancer.

### [ECS Load Balancing Target Groups Target Type](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html#target-type)

When you create a target group, you specify its target type, which determines the type of target you specify when registering targets with this target group.
After you create a target group, you can't change its target type.

- instance
- ip (private ip only)
- lambda
