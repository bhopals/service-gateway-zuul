## Introduction
 API gateways are using to enforce consistent policies and actions on all service calls. 
  - Spring Cloud and Netflix Zuul API gateway.  

## Service gateway implementations

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system or GitHub-based repository.

2.  A Eureka server running as a Spring-Cloud based service.  This service will allow multiple service instances to register with it.  Clients that need to call a service will use Eureka to lookup the physical location of the target service.

3.  A Zuul API Gateway.  All of our microservices can be routed through the gateway and have pre, response and
post policies enforced on the calls.

4.  A organization service that will manage organization data used within EagleEye.

5.  A new version of the organization service.  This service is used to demonstrate how to use the Zuul API gateway to route to different versions of a service.

6.  A special routes services that the the API gateway will call to determine whether or not it should route a user's service call to a different service then the one they were originally calling.  This service is used in conjunction with the orgservice-new service to determine whether a call to the organization service gets routed to an old version of the organization service vs. a new version of the service.

7.  A licensing service that will manage licensing data used within EagleEye.

8.  A Postgres SQL database used to hold the data for these two services.

## Service Gateway resonsibilites
Spring Cloud and Netflix’s Zuul to implement a services gateway. Zuul is Netflix’s open source services gateway implementation.

The service gateway has below responsibilities:

- 1. Put all service calls behind a single URL and map those calls using service discovery to their actual service instances
- 2. Inject correlation IDs into every service call flowing through the service gateway
- 3. Inject the correlation ID back from the HTTP response sent back from the client
- 4. Build a dynamic routing mechanism that will route specific individual organizations to a service instance endpoint that’s different than what everyone else is using


- Spring Zuul acts as Reverse Proxy (Shields Server Instances)

## Building the Docker Images 

Run the following maven command.  

   **mvn clean package docker:build**


## Running the services 

   **docker-compose -f docker/common/docker-compose.yml up**

