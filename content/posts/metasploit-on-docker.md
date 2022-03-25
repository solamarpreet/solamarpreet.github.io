---
title: "Metasploit on Docker"
date: 2022-03-24T19:37:07+05:30
draft: true
ShowToC: false
---

A number of beginners who wish to run Metasploit in a Docker container face difficulty due to lack of official documentation on the matter. Common issues include lack of data persistence across container restarts, port forwarding.

The solution to most of these problems is achieved by understanding Docker's feature set. Because majority of the users attempting to run Metasploit on Docker will be tech literate, Rapid7 expects them to be able to customize their installation to suit their needs.

Let us look at the steps involved in setting up a Metasploit working environment using Docker. 

<br>

### Step 1 - Install Docker

If you haven't installed Docker yet, follow the steps mentioned <a href="https://docs.docker.com/engine/install/" target="_blank">here</a> to install the latest version of Docker for your particular OS.<br> **Note** it is important that you install Docker using the supplied link instead of installing it from your distro's repositories which will be an outdated version.

<br>

### Step 2 - Pull Metasploit from DockerHub

Although we can build our own custom image from scratch, we will use the official Metasploit image supplied by Rapid7 since most people starting out will not require just that.

```shell
docker pull metasploitframework/metasploit-framework
```

If enough people are interested or Rapid7 stops updating their Docker image, I will update this article with steps to build a custom image from scratch.

<br>

### Step 3 - Create a volume for storing data

The official MSF Docker image doesn't create volumes upon initialization so if you want persistent data across container restarts or image updates you will have to create one yourself. Type these commands in a terminal to create 

<br>

### Step 4 - Create a container

Now we need to create a container based on the official Metasploit image that we downloaded earlier. Run the command below

```shell
docker create
```

Note that it is popular to use `docker run` instead of `docker create` in the above command. The docker run command creates a container then immediately starts the container and then finally runs a supplied command inside the container in one go. If no command is supplied it simply creates and then starts the container.

<br>

### Step 5 - Start the container

To start the container you can simply run the following command

```shell
docker start msf
```

<br>

### Optional - Updating MSF

placeholder