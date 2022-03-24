---
title: "Metasploit on Docker"
date: 2022-03-24T19:37:07+05:30
draft: true
ShowToC: false
---

A number of beginners who wish to run Metasploit in a Docker container face difficulty due to lack of official documentation on the matter. Common issues include lack of data persistence across container restarts, port forwarding.<br>
The solution to most of these problems is achieved by understanding Docker's feature set. Because majority of the users attempting to run Metasploit on Docker will be tech literate, Rapid7 expects them to be able to customize their installation to suit their needs.

Let us look at the steps involved in setting up a Metasploit working environment using Docker. If you haven't installed Docker yet, follow the steps mentioned [here](https://docs.docker.com/engine/install/) to install the latest version of Docker for your particular OS.

### 1. Pull Metasploit from DockerHub

We will first pull the latest Metasploit Docker image from DockerHub. Regularly updated and officially supported, this is the easiest way to get started with Metasploit Framework on Docker.

```terminal
docker pull metasploitframework/metasploit-framework
```
