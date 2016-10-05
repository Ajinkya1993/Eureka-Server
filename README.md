# Service Discovery

Service discovery is an important aspect of a microservices architecture.  A
service will register with a central service repository.  The registration
information usually consists of a service name and how to access the service via
the network (a URL).  When another service wishes to use the functionality
provided by a service, the other service will look up the access information
from the central service repository.

# Eureka

Eureka is a service repository created by Netflix.  Netflix released the code
as an open source project.  Sprint Boot provides an easy to use API for
Eureka

The code found in this repository is an Eureka server.  You should be able to
easily build and deploy an Eureka server.

## Configuring
The properties for the Eureka server are found in

    src/main/resources/sample-application.yml

Make a copy of the sample-application.yml file.  Name the copy application.yml.
The application.yml file is ignored by Git to avoid pushing in secret information
to GitHub.

You can edit the application.yml file with any text editor.


## Securing
Spring security is defined as a dependency in the build.gradle file.  This will enable basic authentication for the web services so we are protected when deploying to the cloud.

In the
    src/main/resources/application.yml

fill in random values for the user name and password properties

    security:
      user:
        name: <random user name>
        password: <random password>

Avoid characters that are special to URLS (@, :, /, %, ?).  The user name and password will be used to build URLs to access the services.

## Building
The Eureka server can be built with the following command

    ./gradlew build


## Running Locally
The Eureka server can be started with the following command.

    java -jar ./build/libs/eureka-server-0.1.0.jar

By default, the Eureka server listens on port 8761.  You can access the server
via the following URL

http://localhost:8761

You will be prompted for the user name and password.


## Deploying to CloudFoundry

Fill out a unique name for the name property in the manifest.yml file.

You can deploy the service to CloudFoundry with the following command

    cf push
