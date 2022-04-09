---
title: "How to correctly install Python applications & libraries"
date: 2022-04-09T11:49:39+05:30
tags: ["python", "python3", "pypi", "pip", "pip3", "pipx"]
categories: ["python"]
draft: false
---

It is well known that Python has a problem when it comes to installation of applications since shared libraries can sometimes have significant API changes from one version to another. Added to the complication is the fact that many linux based distros have a preinstalled version of Python that comes with old versions of certain libraries that if overwritten can affect OS stability.

In this guide I will outline the best way to install Python applications & libraries from PyPI without breaking your system and causing a dependency hell.

<br>

## Is the program I am about to install an application or a library?

In the context of installation we define an application as a Python program which exposes a user interface that can be interacted with. For eg. `mitmproxy` and `dockersh` both offer a CLI when called from the terminal which you can use in real time to complete tasks.

Libraries on the other hand are the building blocks of above mentioned applications. They are usually installed on their own only when developing applications or building other libraries. For e.g `requests` and `boto3` can only be imported from within a Python program. Calling them from the terminal serves no purpose.

Sometimes a downloadable package exposes a CLI but also pulls in libraries that you can use in your programs to build new tools. Examples of such hybrid packages are `Impacket`. When dealing with such a package you should look at the purpose you require the package for. Do you wish to use it's CLI or do you wish to use the modules it provides to build an application? Depending on this purpose the method of installation changes as described below.

<br>

## Installing applications

The best way to install Python applications going forward is using `pipx`. On an Ubuntu system simply type the following in the terminal
```sh
sudo apt install python3-pip pipx
```
```sh
python3 -m pipx ensurepath
```
`pipx` allows you to run Python applications by installing them in isolated environments along with their dependencies. If your distro's package repository doesn't contain `pipx` you can visit this [link](https://pypa.github.io/pipx/installation/) and find installation instructions for your platform.


- ### Apps that don't require root privileges

Applications that don't require root privileges can be installed using the following command
```sh
python3 -m pipx install PACKAGE
```
In the above command replace `PACKAGE` with the name of the package you wish to install. For eg. `python3 -m pipx install mitmproxy`

- ### Apps that require root privileges

For applications that require root privileges use the following command
```sh
sudo PIPX_HOME=/opt/pipx PIPX_BIN_DIR=/usr/local/bin python3 -m pipx install PACKAGE
```
In the above command replace `PACKAGE` with the name of the package you wish to install. For eg. `sudo PIPX_HOME=/opt/pipx PIPX_BIN_DIR=/usr/local/bin python3 -m pipx install dockersh`

<br>

## Installing libraries

Since isolated installation of libraries are only really done during development you should only be installing them inside of python virtual environments. To get started we first need to install `venv` on our system.

```sh
sudo apt install python3-venv
```
<br>

Then we will create a new folder that will hold our project and then we will configure a virtual environment inside of it.

```sh
mkdir myproject & cd myproject
```
```sh
python3 -m venv myproject-venv
```

> _Be sure to add the `myproject-venv/` folder to `.gitignore` if you are using git based workflows._

<br>

To begin development you need to activate the virtual environment which can be done by
```sh
source myproject-venv/bin/activate
```

This will change your prompt to `(myproject-venv) user@mycomputer:~/myproject$` which signifies that the virtual environment is currently active.

<br>

You can now install any library from pip and it will be installed in the current virtual environment only without affecting your system or any other application.

```sh
python3 -m pip install PACKAGE
```

<br>

Finally when you are done with development work and wish to revert back to your regular system, simply enter `deactivate` at the terminal.

```sh
deactivate
```

<br>

- ### Using sudo inside a virtual environment

A lot of times the application you are building or a component library requires root privileges to work correctly. In order to use `sudo` inside a virtual environment it has to be called differently than usual.

```sh
sudo -s "PATH=$PATH" python3 main.py
```
This will ensure that the sudo uses the current virtual environment's Python interpreter than the system's interpreter.

<br>

## Conclusion

Note that in the above commands we always invoke `pip`, `pipx` and `venv` as python modules like `python3 -m pipx --version` instead of `pipx --version`. Always invoke these tools in this manner as the latter method can result in unexpected behaviour sometimes. The practices described above should serve adequately for most users. They will only slightly change if you are working with `pyenv` or a recent version of Python that you installed on your own. If you have any queries feel free to reach out to me at [solamarpreet@protonmail.com](mailto:solamarpreet@protonmail.com)