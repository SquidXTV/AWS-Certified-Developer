# [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

## [CloudFront Origin](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/DownloadDistS3AndCustomOrigins.html)

When you create a distribution, you specify the origin where CloudFront sends requests for the files.
You can use several different kinds of origins with CloudFront. For example, you can use an Amazon S3 bucket,
an Application Load Balancer, or an AWS Lambda function URL. When you create your CloudFront distribution,
CloudFront automatically configures most distribution settings for you, based on your content origin type.

## [CloudFront Origin Groups](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/DownloadDistS3AndCustomOrigins.html#concept_origin_groups)

You can specify an origin group for your CloudFront origin if, for example, you want to configure origin failover
for scenarios when you need high availability. Use origin failover to designate a primary origin for CloudFront
plus a second origin that CloudFront automatically switches to when the primary origin returns specific HTTP status code failure responses.
