# Docker commands

## subcommands
- 'object-type' 'command' 'option'
- e.g object-type container, image, network or volume
- e.g command run, attach, commit
- e.g options have to use --publish 

## container
### ls
- ls -la to list all containers including stopped
- ls will only list current running containers
### naming
- CONTAINER ID 64 character long string
- Name : two random words
- rename: docker container rename 'container id' 'new name'
### start & restart
- docker container start/restart 'container identifier'
### create 
- 'container create' creates a container from a given image
### remove & prune
- remove dangling 'docker container rm container id'
- 'docker container prune' removes all dangling container
- --rm  removes after start
### running 
- 'docker container run --rm -it ubuntu'

### executing
- 'docker container run imagename command' 
- e.g docker container run --rm busybox sh -c "echo -n my-secret | base64" 

### volume 

- bind mount 
- --volume 'localfile_system_absolute_path':'container_fs_directory_absolute_path:'read_write_access' 
- docker container run --rm -v $(pwd):/zone ubuntu bash

## Image
### building 
- create a Dockerfile
- docker image build  . 
- docker image build --tag custom-nginx:packaged 
- docker run 'image id' 
- --tag 'image repository:image tag'docker image tag 'image repository:image tag new image repository:new image tag'
- 
### ls
### prune & remove
### layer history 
- docker image history
- each RUN creates a layer

## DockerFile
- pass --file Dockefile.dev ( if file name is not Dockerfile)

## Volume Mount
### Bind
### Named
### Anonymous 


## MultiStage build
- FROM node-lts:alpine as builder

## Network
- docker network ls
- host, bridge, none, overlay , macvlan
- user defined bridge is prefered as they give automatic DNS resolution betweekn container names
- docker network connect "network name"
- docker container run --network 
- docker network disconnect
- docker network rm 

# Docker compose
## Each container is a service
