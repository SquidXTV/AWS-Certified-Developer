# [AWS CodeArtifact](https://docs.aws.amazon.com/codeartifact/latest/ug/welcome.html)

AWS CodeArtifact is a secure, highly scalable, managed artifact repository service that helps organizations
to store and share software packages for application development. You can use CodeArtifact with popular
build tools and package managers such as the NuGet CLI, Maven, Gradle, npm, yarn, pip, and twine.

## [CodeArtifact Asset](https://docs.aws.amazon.com/codeartifact/latest/ug/codeartifact-concepts.html#welcome-concepts-asset)

An asset is an individual file stored in CodeArtifact that's associated with a package version, such as an npm .tgz file or Maven POM and JAR files.


## [CodeArtifact Domain](https://docs.aws.amazon.com/codeartifact/latest/ug/codeartifact-concepts.html#welcome-concepts-domain)

Repositories are aggregated into a higher-level entity known as a domain. All package assets and metadata are stored in the domain,
but they are consumed through repositories. A given package asset, such as a Maven JAR file, is stored once per domain, no matter
how many repositories it's present in.


## [CodeArtifact Repository](https://docs.aws.amazon.com/codeartifact/latest/ug/codeartifact-concepts.html#welcome-concepts-repository)

A CodeArtifact repository contains a set of package versions, each of which maps to a set of assets.
Repositories are polyglot, a single repository can contain packages of any supported type.
Each repository is a member of a single domain and can't be moved to a different domain.


## [CodeArtifact Package](https://docs.aws.amazon.com/codeartifact/latest/ug/codeartifact-concepts.html#welcome-concepts-package)

A package is a bundle of software and the metadata that is required to resolve dependencies and install the software.
