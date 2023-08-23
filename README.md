

# Microservices Notes App

The purpose of the app was to learn:
* writing microservices in Golang,
* data exchange using RPC and gRPC protocols, 
* CQRS pattern.

This repo is built using git submodules.

![Diagram](https://github.com/gavronski/microservices-app/blob/main/diagram.png)


Front-end service communicates with services via the broker.
Broker pushes messages to the Rabbit MQ, so that asynchronous modify data. The listener service receives events from Rabbit MQ and sends them to the notes service. Broker also contains a gRPC client which sends requests for a single note's data to the gRPC server in the notes service. Broker provides an RPC client that sends requests for a list of notes to the RPC server in the notes service.


## Demo
http://206.189.61.93:8082/

## Installation

1. Download the app with submodules content

```bash
git clone https://github.com/gavronski/microservices-app.git --recurse 
```
2. Change directory to the project-clip.
```bash 
cd project-clip
```
3. Start the services defined in the docker-compose file.
```bash
docker-compose up -d --build 
```
4. Open notes container cli 
```bash
docker exec -it notes_container_name shell_name
```
then, run migrations.
```bash
soda migrate
```
5. Open the app at the address 
```bash 
localhost:8082
``` 



