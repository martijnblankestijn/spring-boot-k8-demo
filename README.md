# Spring Boot 2 Application running on K8

## Gradle Tasks

- `gradle bootRun` for running the Spring Boot application
- `gradle dockerBuildImage` for building the docker image
- `gradle dockerPushImage` for pushing the image to my private Docker registry

### gradle dockerPushImage
You need to specify the properties `dockerHubUsername` and `dockerHubPassword`.
See the [Gradle docs](https://docs.gradle.org/current/userguide/build_environment.html).

This can be done through the global gradle properties file in `~/.gradle/gradle.properties`.
Like 

```properties
dockerHubPassword=xxx
dockerHubUsername=xxx
```

Or it can be done through the command line like:

```gradle dockerPushImage -PdockerHubUsername=[username] -PdockerHubPassword=[password]```


## Running on local Kubernetes

To check what the current configured clusters/contexts are:

``` kubectl config view```

To show the current context:

```kubectl config current-context```

## Continuous Integration

Used [CircleCI](https://circleci.com/). Needed to specify the following Environment Variables:

- DOCKER_HUB_USERNAME
- DOCKER_HUB_PASSWORD
