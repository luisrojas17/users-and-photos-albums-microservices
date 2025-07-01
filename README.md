# user-and-photo-album-microservices

This repository contains a couple of microservices:

1. users-microservice
2. photo-albums-microservice

## How to Run the Application
**Note: [You have to start Kafka containers before starting application.](#How-to-Start-Kafka-Containers)**

To start the application from command line you can use next commands:

Using Java jar command:

    ** java -jar target/users-microservice-1.0.0.jar
    ** java -jar target/photo-albums-microservice-1.0.0.jar

Where X means number module that you can run. For example:

    ** java -jar target/users-microservice-1.0.0.jar
    ** java -jar target/photo-albums-microservice-1.0.0.jar

Using Maven with Spring Boot plugin and specific profile:

    ** mvn spring-boot:run -Dspring-boot.run.arguments=--spring.profiles.active=dev

    ** Note: Where dev means development profile.

However, it is necessary to add next plugin to your pom.xml file:

```
...
<build>
    <plugins>
    ...
        <plugin>
		    <groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-maven-plugin</artifactId>
		</plugin>
    ..
    </plugins>
</build>
...
```

## How to Create and Publishing an Image
To create and publish the image you can use next commands:
    
1. docker login

2. docker build -t docker_user_account/docker_repository -f PATH_TO_DOCKERFILE .

3. docker push docker_user_account/docker_repository:tagname

Where docker_user_account is your docker user account and docker_repository is your docker repository.

Go to users-microservice directory and run the following commands:

    docker build -t luisrojas17/users-microservice -f docker/dockerfile .
    
    docker push luisrojas17/users-microservice:latest

Go to photo-albums-microservice directory and run the following commands:

    docker build -t luisrojas17/photos-albums-microservice -f docker/dockerfile .

    docker push luisrojas17/photos-albums-microservice:latest

## How to List all Images
To list images you can use next commands:

    docker images

## How to Delete an Image
To delete an image you can use next commands:   

    docker rmi -f luisrojas17/users-microservice:latest
    docker rmi <IMAGE_ID>