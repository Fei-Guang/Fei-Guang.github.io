The main point of a Content Distribution Network (CDN) is to put the content as close to the end-user as possible, thereby reducing the Distance component of the Round Trip Time (RTT) and speeding up the request. Simply serving static content from a s# sub-domain for CDN.

The advantages of serving content from such a sub-domain, however, are that

The sub-domain can be a cookie-less domain

If you use your cookies correctly (ie. don't have any *.mydomain.com cookies), you can dramatically reduce the size (ie. number of packets sent) of the HTTP request, which would save on bandwidth and speed up requests significantly if you use cookies heavily on the main site.
The page can benefit from a more simultaneous requests being made by the browser

Most browsers will make simultaneous requests for page assets, like images, fonts, CSS, etc. The catch is that most browsers will only allow a limited number of open requests to a particular domain (somewhere around 5 I think). By spreading your assets across multiple sub-domains, you "trick" the browser, and allow more parallel requests, since the limit applies to each sub-domain.


# Adding an Alternate Domain Name Using the CloudFront 
Configure the DNS service for the domain to route traffic for the domain, such as example.com, to the CloudFront domain name for your distribution, such as d111111abcdef8.cloudfront.net. The method that you use depends on whether you're using Amazon Route 53 as the DNS service provider for the domain:

Amazon Route 53
Create an alias resource record set. With an alias resource record set, you don't pay for Amazon Route 53 queries. In addition, you can create an alias resource record set for the root domain name (example.com), which DNS doesn't allow for CNAMEs. For more information, see Routing Queries to an Amazon CloudFront Distribution in the Amazon Route 53 Developer Guide.

Another DNS service provider
Use the method provided by your DNS service provider to add a CNAME resource record set to the hosted zone for your domain. This new CNAME resource record set will redirect DNS queries from your domain (for example, www.example.com) to the CloudFront domain name for your distribution (for example, d111111abcdef8.cloudfront.net). For more information, see the documentation provided by your DNS service provider.

Important
If you already have an existing CNAME record for your domain name, update that resource record set or replace it with a new one that points to the CloudFront domain name for your distribution.
In addition, confirm that your CNAME resource record set points to your distribution's domain name and not to one of your origin servers.


## steps to add cname record

step 1: edit cloudfront distribution then add a Alternate Domain Name for cloudfront  
step 2: add a CNAME resource record set by the DNS service provider
