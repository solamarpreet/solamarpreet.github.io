---
title: "Metasploit on Docker"
date: 2022-03-24T19:37:07+05:30
draft: true
ShowToC: false
---

A number of beginners who wish to run Metasploit Framework in a Docker container face difficulty due to lack of official documentation on the matter. Common issues include lack of data persistence across container restarts, port forwarding.

The solution to most of these problems is achieved by understanding Docker's feature set. Because majority of the users attempting to run Metasploit on Docker will be tech literate, Rapid7 expects them to be able to customize their installation to suit their needs.

Let us look at the steps involved in setting up a Metasploit working environment using Docker. 

<br>

### Step 1 - Install Docker

If you haven't installed Docker yet, follow the steps mentioned <a href="https://docs.docker.com/engine/install/" target="_blank">here</a> to install the latest version of Docker for your particular OS.<br> **Note** it is important that you install Docker using the supplied link instead of installing it from your distro's repositories which will be an outdated version.

<br>

### Step 2 - Pull Metasploit and PostgreSQL from DockerHub

Although we can build our own custom image from scratch, we will use the official Metasploit image supplied by Rapid7 since most people starting out will require just that.

```shell
docker pull metasploitframework/metasploit-framework
docker pull postgres
```

If enough people are interested or Rapid7 stops updating their Docker image, I will update this article with steps to build a custom image from scratch.

<br>

### Step 3 - Create volumes for storing data

Since we will require persistent data across container restarts and/or image updates we will create volumes which will store our data.

```shell
cd ~
mkdir .msf4
mkdir .msf4/database
```

While this will work for most users, anyone who requires multiple containers with each container having separate instances of data one can simply create multiple folders with different names.

<br>

### Step 4 - Create a Docker network

Now we need to create a Docker network that our containers will use for communicating with each other. While not necessary it is useful as it provides isolation for your project & containers

```shell
docker network create --subnet=10.10.10.0/24 msfnet
```

In the above command we are creating a network named msfnet which has a network address range from 10.10.10.1-254

<br>

### Step 5 - Create a PostgreSQL container

Now we shall create a container based on the official PostgreSQL image that we downloaded earlier. Run the command below

```shell
docker create -d --ip 10.10.10.2 --network msfnet --name pgsql -v $HOME/.msf4/database:/var/lib/postgresql/data -e POSTGRES_PASSWORD=password -e POSTGRES_USER=user -e POSTGRES_DB=msfdb postgres:latest
```

In the above command we are creating a container named `pgsql` having the ip address `10.10.10.2` on `msfnet` network. We are also mapping the `.msf4/database` folder we created earlier to the `/var/lib/postgresql/data` folder that sits inside the container. Finally we are setting credentials for the postgresql application running inside the container and creating a database named `msfdb` which will act as the datastore.

Note that it is common to use `docker run` instead of `docker create` in the above command. The docker run command creates a container then immediately starts the container as well.

<br>

### Step 6 - Create a Metasploit Framework container

To create a container with the necessary parameters run the command below

```shell
docker create -it --ip 10.10.10.3 --network msfnet --name msf -v $HOME/.msf4:/home/msf/.msf4 -p 8500-8600:8500-8600 -e DATABASE_URL='postgres://user:password@10.10.10.2:5432/msfdb' metasploitframework/metasploit-framework
```

In the above command we are creating a container named `msf` having the ip address `10.10.10.3` on `msfnet` network. We are also mapping the `.msf4` folder we created earlier to the `/home/msf/.msf4` folder that sits inside the container. 
The `-p` flag maps the 8500-8600 port range of our machine to the same port range of the `msf` container which is necessary to receive reverse shells.
Finally we are setting an environment variable called `DATABASE_URL` that connects the framework to the `pgsql` container we created earlier.

Important to note is the `-it` flag present in above command which is necessary for interactive command line applications such as Metasploit Framework.

<br>

### Step 7 - Start the containers

To start the containers you can simply run the following commands

```shell
docker start pgsql
docker start -i msf
```

Since our data lives separately in the `.msf4` folder, we can safely update base images and create new containers as we require without it affecting data.

<br>

### Optional - Automating the entire above process

By utilising Docker Compose we can automate the entire process described above very easily.
<script src="https://gist.github.com/solamarpreet/24dd9999136c78e6c8b5f469a07bd204.js"></script>
