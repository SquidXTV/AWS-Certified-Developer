# [AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html)

AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code,
runs unit tests, and produces artifacts that are ready to deploy.

## [CodeBuild Buildspec](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html)

A buildspec is a collection of build commands and related settings, in YAML format, that CodeBuild uses to run a build.
You can include a buildspec.yml as part of the source code or you can define a buildspec when you create a build project.


## [CodeBuild Cache Builds](https://docs.aws.amazon.com/codebuild/latest/userguide/caching-s3.html)

You can save time when your project builds by using a cache. A cache can store reusable pieces of your build environment
and use them across multiple builds. Your build project can use one of two types of caching: Amazon S3 or local.
If you use a local cache, you must choose one or more of three cache modes: source cache, Docker layer cache, and custom cache. 
