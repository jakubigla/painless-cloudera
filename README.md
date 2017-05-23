# Painless Cloudera

This repository will allow you to run a single-node deployment of the Cloudera open-source distribution using Docker.
To maximise docker experience, this project takes advantage of `docker-machine` and `docker-compose` tools.
  
## Prerequisites

The only requirement here are Docker stack and VirtualBox
* https://docs.docker.com/engine/installation/
* https://www.virtualbox.org/wiki/Downloads

## Setup

Even though this step is optional, it's recommended to create a separate `docker machine` for Cloudera, given how many resources it consume.
 
```bash
docker-machine create cloudera -d virtualbox --virtualbox-cpu-count 1 --virtualbox-memory 4096
```
This command will create a `boot2docker` 4GB memory and 2 CPU Virtual Machine. Please adjust resources allocation based on your needs. 

Now attach docker client to your terminal:
```bash
eval "$(docker-machine env cloudera)"
```

Add an entry to your host file, so you can access GUI from your browser
```bash
echo -e "$(docker-machine ip cloudera)\tquickstart.cloudera" | sudo bash -c 'cat >> /etc/hosts'
```

## Run

Please run your docker-compose file:
```bash
docker-compose up -d
```

## Todo

* Break down Cloudera image to separate services to take advantage of `docker-copmose` tool. 