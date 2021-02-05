# Technical Test

## Introduction

The assignment is divided into three tasks.

### Task 1: Create a DOCKERFILE

-   You are expected to put the application in a container so that it runs.

### Task 2: Create a Docker-compose

-   You are expected to write a docker-compose-yml
-   The compose file should bootstrap all dependecies of the service so that the service can reach them at "redis" and "kafka"
-   The entire infra should be running with a single \`doocker compose up\` statement.
-   The dependecies of the services are 
    -   **Kafka:** reachable at "kafka:9092"
    -   **Redis:** reachable at "redis:6379"
-   Mount the data directory of redis and kafka to a local directory(ies) in the docker-compose file.

### Task 3: Deploy service using CloudFormation OR Terraform

-   Write a CloudFormation/Terraform Temlplate so that we may deploy the application container using ECS
-   Expect redis and kafka to be running at \`redis\` and \`kafka\` endpoints.
-   Use your best judgement to set CPU and Memory requirements
-   Use your best judgement for LoadBalancer and Target Group configuration.
-   Assume that we have stored the Docker Image in a Container Repository and ECS can pull the Docker Image with no issues.


## Expectation

-   You are not expected to edit the code.
-   All the additional infrastructure that you need to deploy a service in ECS like VPC-id, Subnet-id, ClusterName etc would be already available and you can use placeholder values for them in your CloudFormation/Terraform template.


## Goals

-   The goal of this exercise is get a clear picture of how much you understand docker, docker-compose and aws-services.


## Notes

-   We believe that there is enough information in this document and the README.md file for you to successfully complete the tasks.
-   That said, if you have questions; please feel free to ask them.
-   If we have missed anything and you make assumptions for them, please mention the assumtions that you are making.


## How to Submit this assignment ?

-   Create a repository in gitlab/github and share the URL with us.
-   Write a README that shows how to deploy the application using the template.




# Go Redis Kafka Demo

A demo application that interacts with Kafka (producer & consumer) + Redis

This application has 2 parts
1. **http-server**
2. **kafka-consumer**

The http-server handles 2 routes

1. http://127.0.0.1:8080/produce - this produces an event on kafka of the shape `{ type: "number", number: 123333 }` the kafka-consumer listens to this event and determines whether the number is odd/even and based on that increments (`incr`) a key in redis
2. http://127.0.0.1:8080/ - gives you statistics like `{"requests":12,"even":5,"odd":7}` number of events/requests processed so far, number of odd numbers, number of even numbers

  
# To run this project
 
1. [Install go](https://www.tecmint.com/install-go-in-linux/) & [setup your development environment](https://golang.org/doc/code.html)
2. Install Redis
3. Install Kafka & make a topic call `numbers` (you can name the topic something else also; but make sure the name of the topic is correct in `start.sh`)
4. RUN `./start.sh`

the `start.sh` contains enviroment variables you need to handle it according to you convinence