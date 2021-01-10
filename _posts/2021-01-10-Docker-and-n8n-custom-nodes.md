---
title: Docker and n8n custom nodes
layout: post
categories: [Automation, n8n]
image: /assets/img/posts/n8n-custom-nodes.png
description: "Play with custom nodes on n8n docker environment"
customexcerpt: "Play with custom nodes on n8n docker environment"
---

!(custom node)[https://non0.blog/assets/img/posts/n8n-custom-nodes.png]


You have developed your own node and you want to test it on your n8n instance running on docker, let's see how to do this!

* hello
{:toc}


## Prerequisite

(This is what I used)

- Ubuntu 18.04 (running on AWS)
- n8n instance running on Docker
- Your node *(built or not)*

    
## Build your custom nodes

If you didn't build your node before, you can do it with n8n-node-dev command :

```
ubuntu@aws_IP:~/factory_n8n$ n8n-node-dev build

Build credentials and nodes
=========================
The nodes got build and saved into the following folder:
/home/ubuntu/.n8n/custom
```

Your node is now built for n8n and files are located in your n8n directory as you can see in the returned message.

You will find for each file 3 new files *(whatever your original files : node, credentials or script file linked to your node)*, example :

- If you build a node called "mynode.node.ts" :
  - mynode.node.d.ts
  - mynode.node.js
  - mynode.node.js.map
  
## Organize your docker volume

If you have followed the official tutorial to launch your n8n instance with Docker ([https://docs.n8n.io/reference/server-setup.html#_5-create-docker-compose-file](https://docs.n8n.io/reference/server-setup.html#_5-create-docker-compose-file)), you have mounted a volume based dedicated to n8n :

```yaml
volumes:
      - ${DATA_FOLDER}/.n8n:/home/node/.n8n
```

After to determine where is your data folder, you can create a new directory inside .n8n called "custom" *(it does not exist by default)*.

Once done, move your node files built earlier to this new directory *(with "mv" command)*.

Go to your directory which contains your docker-compose file and restart n8n

```
docker-compose stop #if already launched
docker-compose up -d #detach launched
```

You can now access to your custom node (node/credentials) on your docker instance!
