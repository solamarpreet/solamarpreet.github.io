---
title: "Parallelism and Concurrency in Python"
date: 2022-03-12T12:17:40+05:30
draft: true
ShowToC: false
---

There is a lot of confusion and misunderstanding with respect to the concurrency and parallel processing capabilities of the Python language. Much of this stems from a lack of understanding that Python is ever evolving and rapidly growing in order to acommodate the needs of modern computing. And while it is true that some of these capabilities were not ready for production in the past, the Python community has worked hard to ensure that it is not true as of date.

In order to properly utilize Python's concurrent and parallel features, it is important to understand how these features are implementated from a design standpoint. This is necessary since Python's implementation of concurrency & parallelism is quite different when compared to other languages.


## History
When Python was first released in 1991 general purpose computers had a single CPU core. Most of the programming done up until then was single threaded in nature. Even though computer experts understood the potential of multithreaded computing which would allow tasks to run concurrently, there was a lack of OS support for threads. This changed in 1993 when Windows NT was released which included a scheduler that supported threads. It was a giant leap for computing as the operating system could now run multiple tasks at the same time by making better use of the CPU. Python now had to implement threads in order to keep up with this latest development.
One of the major features of the Python programming language was automated memory management. It achieved this by reference counting. Reference counting however wasnt thread safe. Because a context switch was beyond the control of


We now take a look at the major concurrency & parallelism related libraries available in Python 3 and discuss each of their applications.

### 1. Threading
```py
import threading
```
Due to GIL allowing only a single thread to run at any given instant, the threading module is useful in scenarios involving a large number of I/O bound tasks. Common I/O bound tasks are disk read/write operations, data transmission over a network and waiting for user input. Consider the following example

### 2. Multiprocessing
```py
import multiprocessing
```
The threading module is used to speed up execution of a program that has a large number of I/O bound tasks. Common I/O bound tasks are disk read/write operations, data transmission over a network and waiting for user input. Consider the following example

### 3. Concurrent.Futures
```py
import concurrent.futures
```
The threading module is used to speed up execution of a program that has a large number of I/O bound tasks. Common I/O bound tasks are disk read/write operations, data transmission over a network and waiting for user input. Consider the following example

### 4. Asyncio
```py
import asyncio
```
The threading module is used to speed up execution of a program that has a large number of I/O bound tasks. Common I/O bound tasks are disk read/write operations, data transmission over a network and waiting for user input. Consider the following example