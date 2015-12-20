## What is configuration management?
Configuration management is the process of ensuring that we can set up systems in consistent and well-defined manner. Config management is important to create repeatable and scalable systems. Config management, if done right, lets us setup a large number of servers in a repeatable manner ensuring right versions of software and dependencies, user management, keys etc. A well define config management acts like a blue print of your infrastructure and helps others to understand the details of your systems internals.

## Why do we need config management?
TO understand the need of config management, let us try to understand the steps required to setup a simple web server. You might be tempted to think that all it needs is installing a webserver like Nginx or Apache and a database like MySQL. But take a few minutes and think again.

Steps required to set up a simple web server:
1. Create basic users
2. Setup keys for these users
3. Install basic debugging packages like iotop
4. Install monitoring
5. Install webserver and database software
6. Update the configuration of webserver and database
7. Update firewall rules
8. Create directory structure to hold application
9. Deploy application


Doesn't looks that simple now, right? In theory, we can write scripts to do all the tasks above. However, scripts tend to become ugly and less portable over the time. Config management tools can help you to address all of these issues. Some of the popular tools for configuration management are:

* Ansible
* Puppet
* Chef
* Salt Stack

As an example, we will have a look at Ansible.
## Why Ansible?
Among all the tools that we have evaluated, we love Ansible the most for multiple reasons:
* It does not need any pre-installed management client on the server
* It does not run with root privileges.
* It uses OpenSSH as transport
* Easy to read because it uses YAML
 
## Setup Ansible
Getting Ansible on most of the *nix is easy. Just use default package managers like yum, dnf or apt-get.
However, if you like to play with latest and greatest, then using pip is a good choice.

```# pip install ansible```


