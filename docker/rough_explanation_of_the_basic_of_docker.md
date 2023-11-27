# Rough Explanation Of The Basic Of Docker
https://qiita.com/etaroid/items/b1024c7d200a75b992fc

## Virtualization
Virtualization is the process of setting up another machine virtually on top pf the OS installed on a machine(host OS) such as a PC or a server.  
Simply put, virtualization is "launching a virtual PC inside a PC".

### Conventional Virtualization
Conventional virtualization uses a virtualization software to launch a virtual machine/guest OS on top of the host os, build a middleware environment in that virtual machine, and execute a program to run applications
```
[
  Virtual Machine
  [Application]
  [Middleware]
  [Guest OS]
]
[Virtualization Software]
[Host OS]
[Hardware]
```
### Container-based Virtualization
Docker offers container-based virtualization.The docker engin running on top of the host OS creates an execution environment with a middleware environment called a "container" and runs an application in it without booting a guest OS.

## Advantages of Docker
- lightweight operation
- Easy sharing of execution environment(Dockerfile, image, Docker Hub(share images))
- Compatibility across different OS

## Elements of Docker
### Docker engine
Docker engine is a resident program for using Docker. By installing a software such as Docker for Mac, Docker for Windows on your PC, the Docker engine will run as a resident program and allowing you to use docker.

### Image
- A collection of configuration files required to start a container(=application execution environment).
- Image is a binary file.  
- An image is a template for a container.
- Versioned by tags
  - nginx:latest
  - nginx:1.14-perl
  - If no tag name is specified, the "latest" tag is automatically used.
- Once an image is created, it cannot be edited.
### The structure of a image
An image has a layered structure.
```
Image
[
  middleware(binaries, libraries)
  [layer2(Ruby)]
  [layer1(CentOS)]
]

↓

[
  container
  [application]
  [
    middleware
    [container layer] read/write
    [layer2(Ruby)] read only
    [layer1(CentOS)] read only
  ]
]
```
For example, if Ruby on Rails is installed in the container, it will be stored in the container layer. The contents of the container layer will be stored in the storage of Docker on the host OS.

## Data management in Docker
### Volume
- A method to mount the specific directory(/var/lib/docker/volumes), which is automatically generated on the host machine, to the container.
- Mounted volumes directory should not be manipulated directly from the original directories on the host.
- Different containers on the same host machine can share files by mounting the same volume.
- If a volume is shared by multiple containers, editing privileges can be set for each containers.
- Volumes remain after the containers are deleted. docker volume rm volumeName command can delete the volumes.

### Bind mount
- A method of mounting any directory on the host machine. The directory on the host machine can be manipulated directly.
- If the mount source directory doesn't exist, an error will occur. So it must be created beforehand.
- If an empty directory on the host is mounted to /user or other directory in the container, the data in the container will be lost and the container may not work properly.
- Editing privileges can be set for each containers.

### tmpfs
- A method to mount the memory area of the host machine to the container.
- Whether the host machine terminates or the container terminates, the data is released.

## Docker network
Connect and communicate with multiple containers.

### Bridge network
Bridge network is the network that exists by default.
- Communicate with containers that exist in the same network by IP addresses.
- Containers cannot communicate by the container names because DNS is not defined in bridge network.

### Host network
Host network is the network that exists by default.
- Containers uses the network stack of the host machine.
- Containers share IP addresses and ports with the host machine and behave the same way as the host machine.

### None network
None network is a network mode which no network interface is assigned to a particular container. Containers launched in this mode are completely cut off from external network connections to other containers.

### Original network
Creating an original network allows containers to communicate with other containers by container names.

## Docker Compose
Docker Compose is a tool to define and run multiple containers.
### How to use Docket Compose
- Prepare a Dockerfile
- Write docker-compose.yml
- Run `docker compose up` command in the directory where the yml file is located