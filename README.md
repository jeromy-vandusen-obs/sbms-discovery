# Spring Boot Microservices - Service Discovery

## Jenkins Job Configuration

1. On the main Jenkins dashboard page, click "New Item".
2. Enter "sbms-discovery" in the "name" field, select "Pipeline", and click "OK".
3. Scroll down to the "Pipeline" section and in "Definition" select "Pipeline script from SCM".
4. In "SCM", select "Git".
5. In "Repository URL", enter "https://github.com/jeromy-vandusen-obs/sbms-discovery.git".
6. Deselect "Lightweight checkout" and click "Save".

## Profiles

To run locally for development purposes, use the `dev` profile.

To run in a Docker swarm, use the `swarm` profile.

## Environment variables

* EUREKA_INSTANCE_LIST: A comma-separated list of Eureka discovery service URLs. The default value is
`http://localhost:8761/eureka/`.

## To Do

* Add security.
* Verify configuration properties in `swarm` profile. In particular, confirm that `hostName` and `instanceId` are needed.
