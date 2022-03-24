---
title: "Metasploit on Docker"
date: 2022-03-24T19:37:07+05:30
draft: true
ShowToC: false
---

A number of beginners who wish to run Metasploit in a Docker container face trouble due to lack of official documentation on the matter. Common issues include lack of data persistence across container restarts, port forwarding.

The solution to most of these problems arrives from understanding Docker's feature set. Because majority of the users attempting to run Metasploit on Docker will be tech literate, Rapid7 expects them to be able to customize their installation to suit their needs.

#### Why isn't the official Metasploit Docker working out of the box?

Docker is a fantastic tool for running software and has revolutionized the way applications are deployed in cloud infrastructure. 