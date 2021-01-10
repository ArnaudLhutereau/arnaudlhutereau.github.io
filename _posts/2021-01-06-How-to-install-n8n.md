---
title: How to install n8n?
layout: post
categories: [Automation, n8n]
image: /assets/img/posts/n8n.png
description: "Want to install n8n? Let's see how to do"
customexcerpt: "You Want to install n8n? Let's see how to do!"
---

![n8n](https://non0.blog/assets/img/posts/n8n.png)

You want to discover and play with n8n? You can follow this tutorial to install n8n where you want (own PC, cloud...). During it, I used AWS but it will work everywhere if you follow all prerequisite ;-)

* hello
{:toc}


## Prerequisite

(This is what I used)

- Ubuntu 18.04 (running on AWS)
- 1 GB RAM
- 8 GB HDD
- Default user "ubuntu"
- Firewall rules in the security group linked to my VM : 
  - Incoming :
    - Allow port 22 (TCP) from my personnal IP (/32) for ssh connection
    - Allow port 5678 (TCP) from my personnal IP (/32) for web ui access
  - Outcoming :
    - Allow all port (all) to 0.0.0.0/0
    
## Configuration & installation

Let's install n8n on a linux VM with ubuntu user.

### Ubuntu

Just to be sure all is OK on the current VM

```
ubuntu@aws_IP:~$ sudo apt-get update
ubuntu@aws_IP:~$ sudo apt-get upgrade
```

### node.js & npm

Firstly, we need to install nodejs. Ubuntu 18.04 does not have the latest node version in his repository, so don't run on "apt install nodejs"!

We will start to add the official repo (I took the 14' version, LTS until april 2023) :

```
ubuntu@aws_IP:~$ wget -qO- https://deb.nodesource.com/setup_14.x | sudo -E bash -
```

Now I can install node.js :

```
ubuntu@aws_IP:~$ sudo apt install -y nodejs
```

To be sure all is good for future node, I will install "build-essential" which is mandatory for some paquets.

```
ubuntu@aws_IP:~$ sudo apt install build-essential
```

I can check the current version with :

````
ubuntu@aws_IP:~$ nodejs -v
v14.15.3

ubuntu@aws_IP:~$ npm -v
6.14.9
````

### Install n8n

Now I can install n8n with npm command :

```
ubuntu@aws_IP:~$ npm install n8n -g
```

But I have an error message about writting access :

 ```
ubuntu@aws_IP:~$ npm install n8n -g
[...]
Missing write access to /usr/lib/node_modules
 ```

After googling it, I changed the npm's default directory as they say in the npm documentation ( https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally ) with :

```
ubuntu@aws_IP:~$ mkdir ~/.npm-global
ubuntu@aws_IP:~$ npm config set prefix '~/.npm-global'
ubuntu@aws_IP:~$ export PATH=~/.npm-global/bin:$PATH
ubuntu@aws_IP:~$ source ~/.profile
```

Now I can retry n8n installation :

```
ubuntu@aws_IP:~$ npm install n8n -g
```

It's works!

I start it with :

```
ubuntu@aws_ip:~$ n8n

UserSettings got generated and saved to: /home/ubuntu/.n8n/config
n8n ready on 0.0.0.0, port 5678
Version: 0.100.0

Editor is now accessible via:
http://localhost:5678/

Press "o" to open in Browser.
```

Now you have a web access to n8n. Remind you that no authentication is required, only your firewall rules protect from unauthorised access!

![n8n web ui](https://non0.blog/assets/img/posts/n8n_web_ui.png)


