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
- Easy sharing of execution environment
- Compatibility across different OS

## Dockerfile
Dockerfile is a set of instructions for creating an image. It contains