# Overview

In this exercise we will learn a bit more into Docker, the underlying virtualization system used by Kubernetes, and learn how get root privileges on a host machine using a docker container.

```mermaid

graph LR;
    A[Non-privileged User] --> |run| B[docker container];
    B[Docker container] --> |escalate| C[sudoer];
```


# Introduction

A docker container is not a VM. It has no Linux kernel running inside of it and only has the filesystem in it if we explicitly copy it into the docker image (a blueprint for containers) from which this container was instantiated. If we don't copy any files inside an image, its size is 0 bytes. 

The most accurate definition of a docker container is a single Linux process to a certain degree isolated from the host system on which it runs. Note that even though there are ways to run more than one process inside of a container, it is an anti-pattern and a system with proper design should avoid it.

## Running a docker image
There is a plenty of docker images out there. You can use an Ubuntu:22.04 image for simplicity. You can attach to a terminal running in any of them by using the command shown in the appendix. All it does is instantiate a container, runs `bash` and attaches a pseudo-terminal to it. 

You can access the paths on the host file system from inside the docker container by using bind mounts.

# Exercise

1. Create a non-root user on a host machine. Give it a password. Make sure that the user can use docker (add him to a docker group). Switch to that user.

2. As of now, you don't have access to sudo on your host machine unless you know the sudo password. Let's chagne that. Pick any image you like and run bash in it. Think how you can access sensitive files on the host filesystem from inside the container.

3. Insider the container, modify `sudoers` on the host file system to allow your non-privileged user invoke `sudo` action without password.

4. Exit the container and validate that your previously non-privileged user is now a sudoer without a password. Congratulatons with a nice privilege escalation attack!

# Appendix A: Helper commands

Run command COMMAND in a container invoked from image IMAGE with an interactive terminal attached to it. `-ti` for interactive shell. `-v a:b` mounts host path `a` to a container path `b`.

```bash
sudo docker run -ti  -v /<host path>:/<inside container path> IMAGE:TAG COMMAND
```

The format is the sudoers file that grants all privileges to username:
```bash
username ALL=(ALL) NOPASSWD: ALL
```