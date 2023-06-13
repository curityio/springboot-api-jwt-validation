# Spring Boot API OAuth Integration

[![Quality](https://img.shields.io/badge/quality-experiment-red)](https://curity.io/resources/code-examples/status/)
[![Availability](https://img.shields.io/badge/availability-source-blue)](https://curity.io/resources/code-examples/status/)

A basic sample to show how to use Spring Boot as an OAuth framework for managing JWT validation.\
After validating the JWT, the controller then uses scopes and claims from the API when serving data.

## Run the API

First ensure that a Java Development Kit of 17 or later is installed.\
Then edit the application.yml file to point to a valid issuer URI:

```yaml
spring:
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: https://idsvr.example.com/oauth/v2/oauth-anonymous
```

## Run the API

Build and run the API with the following command, and the API will listen on port 8080 by default:

```bash
./gradlew bootRun
```

## Call the API

The API requires a valid JWT access token, or it will return a 401 response:

```bash
curl -i http://localhost:8080/services -H "Authorization:  Bearer eyJraWQiOiIxNzQwNDU5OTIxIiwieDV0..."
```

The JWT access token must have a `services:read` scope or the API will return a 403 response.\
If the access token includes a claim containing `role=developer`, then the API returns additional data. 

## Further Information

- See the [Spring Boot API Tutorial](https://curity.io/resources/learn/spring-boot-api/) for a technical walkthrough
- Please visit [curity.io](https://curity.io/) for more information about the Curity Identity Server.
