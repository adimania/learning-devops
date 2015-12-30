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
 
## Ansible Crash Course
We are going to deliver a quick peek into Ansible setup and its way of working.

### Ansible Setup
Getting Ansible on most of the *nix is easy. Just use default package managers like yum, dnf or apt-get.
However, if you like to play with latest and greatest, then using pip is a good choice.

```# pip install ansible```

### Ansible Components
Here are the basic components of an Ansible setup
* **Inventory:** It is a list of servers that Ansible will run on. We can group these servers in logical units and run Ansible on groups simultaneously. Example:
```
[webservers]
server1
[application]
server1
server2
```
* **Variables:** These are ... variables.
* **Tasks:** These are the smallest unit of work in Ansible world. A task can be to create a file or to remove a user or to install a package.
* **Roles:** These are collection of tasks that can be used to achieve an objective end-to-end. For example, setting up Nginx can be a role which in turn will have tasks like installation, starting, setting up config etc.
* **Playbooks:** These are like the programs that encapsulates several roles. For example, setting up a application server may involve Nginx role, passenger role and a common role for installing things like git or iotop.
* **Modules:** These are little (or huge?) plugins that actually do the work. These are similar to libraries (if you are familiar with C/Java) or modules (for python or ruby folks). Every task has to use a module to do *something*. They can be written in a role or a playbook and they can be called directly via command line.
```
$ ansible webservers -m command -a "ls"
```

### Simple Playbook
```
---
- hosts: localhost
  sudo: yes
  vars:
    - server_port: 8080

  tasks:
    - name: install nginx
      yum: pkg=nginx state=installed

    - name: serve nginx config
      template: src=../files/flask.conf dest=/etc/nginx/conf.d/
      notify:
      - restart nginx

    - name: install pip
      yum: name=python-pip state=installed

    - name: install flask
      pip: name=flask

    - name: serve flask app systemd unit file
      copy: src=../files/flask-demo.service dest=/etc/systemd/system/

    - name: fetch application
      git: repo=https://gist.github.com/c454e2e839fcb20605a3.git dest=/opt/flask-demo
      notify:
        - restart flask app

    - name: set selinux to permissive for demo
      selinux: policy=targeted state=permissive

    handlers:
    - name: restart nginx
      service: name=nginx state=restarted

    - name: restart flask app
      service: name=flask-demo state=restarted
```

If you are thinking, *"Hey! Wait! Where is the explanation of this big blob of lines above?"*, then we would say, try reading it once.
