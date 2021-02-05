
# Go Redis Kafka Demo

A demo application that interacts with Kafka (producer & consumer) + Redis


# docker-compose.yaml

It creates 3 containers named kafka, redis,http-server
corresponding ports and environment variables are mentioned

- This uses open source image for redis,kafka and custom image fro http-server(based on go language)

To run : docker-compose up

# cloud-formation.yaml

- This is used to deploy stack on AWS cloudformation which in turn deploys to ECS  
