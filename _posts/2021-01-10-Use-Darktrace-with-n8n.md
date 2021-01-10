---
title: Use Darktrace with n8n
layout: post
categories: [Automation, n8n]
image: /assets/img/posts/darktrace_node.png
description: "How to connect Darktrace with n8n"
customexcerpt: "Get Darktrace data in your n8n workflow!"
---

n8n is a powerfull  workflow automation tool which allows us to create our own nodes for specific tools that we can use everyday.

Thank to the *n8n-node-dev* I worked on a custom node for Darktrace to avoid the utilization of multiple nodes like [Function item](https://docs.n8n.io/nodes/n8n-nodes-base.functionItem/) + [HTTP request](https://docs.n8n.io/nodes/n8n-nodes-base.httpRequest/), to have an all-in-one node.

* hello
{:toc}


#### Features

Darktrace have an API with more than 20 endpoints for a lot of type of request to get and send information.

To not have a big node with a lot of fields when you want to use it, I decided to let the user write his own request with the variable selector. The user have to check what he wants to do with the help of the darktrace API documentation *(/apihelp on DT web interface)*. For example :

- Get last model breachs 
- Get status, time, tags
- Get subnet, metrics
- Modify intelligence feed
- Get models information, pcap, specific information on endpoint (based on filter)
- ...

#### Implementation

I assume that you have installed the node on your n8n instance

1. On Darktrace web interface, create or get your API credentials (public token & private token)
2. On n8n, create a new credentials ans search "Darktrace API"
3. Fill all fields with your information (do not add a "/" at the end of the URL according to the Darktrace documentation)

![Create credentials](https://non0.blog/assets/img/posts/credentials.png)



4. In your n8n workflow, click on "Add node" button and add "Darktrace" *(in regular node)*
5. Select your credentials created at the step 3.
6. Add the date of the request to Darktrace API *(according to the documentation, the date must be within 30 minutes of the Darktrace system time)*
7. Choose your method type
8. Write your request, for example : /modelbreaches?from=2021-01-01T00:00:00.00



The response will be added in a *"dt_request"* variable which contains JSON return, for example I got 6 alerts :



![Responsenode]((https://non0.blog/assets/img/posts/response_example.png)



Once you have all information in n8n, you can send them to other nodes like [TheHive](https://docs.n8n.io/nodes/n8n-nodes-base.theHive/) to open a new alert/case.



#### Useful links

- [Official n8n website](https://n8n.io/), [n8n github repo](https://github.com/n8n-io/n8n), [n8n community](https://community.n8n.io/) : information, node & workflow documentation, support

- [https://your-darktrace-instance/api/help](https://your-darktrace-instance/api/help) : Darktrace api documentation (endpoints, parameters...)

