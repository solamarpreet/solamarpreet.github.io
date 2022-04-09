---
title: "How to correctly install Python applications & libraries"
date: 2022-04-09T11:49:39+05:30
tags: ["python", "python3", "pypi", "pip", "pip3", "pipx"]
categories: ["python"]
draft: true
---

It is well known that Python has a problem when it comes to installation of applications since shared libraries can sometimes have significant API changes from one version to another. Added to the complication is the fact that many linux based distros have a preinstalled version of Python that comes with old versions of certain libraries that if overwritten can affect OS stability.

In this guide I will outline the best way to install Python applications & libraries from PyPI without breaking your system and causing a dependency hell.

## Is the program I am about to install an application or a library?

In the context of installation we define an application as a Python program which exposes a user interface that can be interacted with. For eg. `mitmproxy` and `dockersh` both offer a CLI when called from the terminal which you can use in real time to complete tasks.

Libraries on the other hand are the building blocks of above mentioned applications. They are usually installed on their own only when developing applications or building other libraries. For e.g `requests` and `boto3` can only be imported from within a Python program. Calling them from the terminal serves no purpose.

Sometimes a downloadable package exposes a CLI but also pulls in libraries that you can use in your programs to build new tools. Examples of such hybrid packages are `Impacket`. When dealing with such a package you should look at the purpose you require the package for. Do you wish to use it's CLI or do you wish to use the modules it provides to build an application? Depending on this purpose the method of installation changes as described below.

## Installing applications

The best way to install Python applications going forward is using `pipx`. To install `pipx` in Ubuntu systems simply type the following in the terminal
```terminal
sudo apt install pipx
```
`pipx` is an officially supported tool that allows you to run Python applications in isolated environments.