---
title: "Parallelism and Concurrency in Python 3"
date: 2022-03-12T12:17:40+05:30
draft: true
ShowToC: false
---

There is a lot of confusion and misunderstanding with respect to the concurrency and parallel processing capabilities of the Python language. Much of this stems from a lack of understanding that Python is ever evolving and rapidly growing in order to acommodate the needs of modern computing. And while it is true that some of these capabilities were not ready for production in the past, the Python community has worked hard to ensure that it is not true as of date.

We will take a look at the major concurrency & parallelism related libraries available in Python 3 and discuss each of their applications. 

### 1. Threading

The threading module is used to speed up execution of a program that has a large number of I/O related tasks. Common I/O related tasks are disk read/write operations, data transmission over a network and waiting for user input. Consider the following example