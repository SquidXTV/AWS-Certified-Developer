# [Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html)

Amazon Route 53 is a highly available and scalable Domain Name System (DNS) web service.
You can use Route 53 to perform domain registration, DNS routing, and health checking.
 
## [Route 53 Domain Registration](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar.html)

When you want to get a new domain name, such as the example.com part of the URL http://example.com, you can register it with Amazon Route 53.
You can also transfer the registration for existing domains from other registrars to Route 53 or transfer the registration for domains that
you register with Route 53 to another registrar. 


## [Route 53 Domain Name System (DNS)](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/route-53-concepts.html#route-53-concepts-domain-name-system-dns)

A worldwide network of servers that help computers, smart phones, tablets, and other IP-enabled devices to communicate with one another.
The Domain Name System translates easily understood names such as example.com into the numbers, known as IP addresses,
that allow computers to find each other on the internet.


## [Route 53 Authoritive Name Server](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/route-53-concepts.html#route-53-concepts-domain-name-system-dns)

Route 53 name servers are the authoritative name servers for every domain that uses Route 53 as the DNS service.
The name servers know how you want to route traffic for your domain and subdomains based on the records that you created in the hosted zone for the domain.


## [Route 53 Hosted Zone](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/route-53-concepts.html#route-53-concepts-domain-name-system-dns)

A hosted zone is a container in that stores the DNS records for a domain or subdomain. 
A public hosted zone is reachable from the public internet. A private hosted zone is only resolvable inside selected VPCs.


## [Route 53 DNS Record](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/route-53-concepts.html#route-53-concepts-domain-name-system-dns)

An object in a hosted zone that you use to define how you want to route traffic for the domain or a subdomain.

### [A Record](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/ResourceRecordTypes.html#AFormat)

You use an A record to route traffic to a resource, such as a web server, using an IPv4 address in dotted decimal notation.


### [AAAA Record](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/ResourceRecordTypes.html#AAAAFormat)

You use an AAAA record to route traffic to a resource, such as a web server, using an IPv6 address in colon-separated hexadecimal format.


### [CNAME and Alias](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/ResourceRecordTypes.html#CNAMEFormat)

A CNAME record maps DNS queries for the name of the current record, such as acme.example.com, to another domain (example.com or example.net)
or subdomain (acme.example.com or zenith.example.org). 

Amazon Route 53 also supports alias records, which allow you to route queries to selected AWS resources, such as CloudFront distributions and Amazon S3 buckets.


### [TXT Record](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/ResourceRecordTypes.html#TXTFormat)

A TXT record contains one or more strings that are enclosed in double quotation marks (").



## [Route 53 Routing Policy](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/route-53-concepts.html#route-53-concepts-domain-name-system-dns)

A setting for records that determines how Route 53 responds to DNS queries.

### [Simple Routing Policy](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-simple.html)

With simple routing, you can set up standard DNS records, with no special Route 53 routing such as weighted or latency.
You typically route traffic to a single resource, for example, to a web server for your website. 


### [Failover Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-failover.html)

With failover routing, you can route traffic to a resource when it's healthy or to a different resource when the first one is unhealthy.
The primary and secondary records can route traffic to anything from an Amazon S3 bucket set up as a website to a complex tree of records.


### [Geolocation Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-geo.html)

With geolocation routing, you can choose the resources that serve your traffic based on where your users are located (continent, country, state),
meaning the location that DNS queries come from.


### [Geoproximity Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-geoproximity.html)

With geoproximity routing, Amazon Route 53 routes traffic to your resources based on the location of your users and your resources.
It sends traffic to the closest available resource.


### [Latency-based Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-latency.html)

If your application is hosted in multiple AWS Regions, you can improve performance for your users by serving their requests from the AWS Region with the lowest latency. 


### [IP-based Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-ipbased.html)

With IP-based routing in Amazon Route 53, you can fine-tune your DNS routing based on your knowledge of your network, applications, and clients.
This helps you make the best DNS routing choices for your end users.


### [Multivalue Anwer Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-multivalue.html)

With multivalue answer routing, you can set up Amazon Route 53 to return multiple values, such as IP addresses for your web servers, in response to DNS queries.
You can specify multiple values for almost any record, but with multivalue answer routing, you can also check the health of each resource.
Route 53 then returns only values for healthy resources.


### [Weighted Routing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-weighted.html)

With weighted routing, you can link multiple resources to a single domain name (example.com) or subdomain name (acme.example.com)
and choose how much traffic goes to each resource.
