+++
date = '2025-12-09T21:45:48Z'
draft = true
title = 'Self Hosting on a MacBook 2012'
+++
# How I built my homelab on a MacBook 2012

## Overview
I have local Linux servers for learning and testing ideas, and I also run some application in the cloud.
Self hosting is complex, time consuming  and requires technical knowledge to bring together different components and application and create a harmonious usable platform.  

### Purpose 
The main objective is to continue learning, push myself to explore advance sysadmin/devops concepts and dig deeper into Linux and open source technologies. Eventually, I would like to self host and manage services that can enable businesses and community projects.
In this post, I am going to share the nature and structure of my current homelab, how it came about, what I did,  what worked, what didnt and how I worked around the challenges. In future posts, I am going to expand to include other projects.

### Practice makes an IT Practitioner
I mentioned servers running in the cloud but in general my IT experience is and has always been on a small budget.  I started with VMs on a Windows machines, dual booting Linux, standalone local servers to running applications in the cloud.  

#### *Hardware*
Like any serious tinkerer, I have a lot of hadware, usually other people’s castoffs. Many a times I repurpose or canibalise parts to upgrade laptops into linux machines.
Based on this practice, I have acquired a few dated hardware:
1.	MacBook 2012,1000GB SSD, 8GB RAM (previous owners:  friend’s teenage son)
2.	Mac mini (Late 2012), 256 GB SSD, 8 GB RAM (previous owner: husband’s friend)
3.	MacBook Pro (Early 2015), 500GB SSD, 16GB RAM (refurbished form Backmarket)
4.	WD Blue 500GB SSD (bought as upgrade for previous old laptop)
5.	Some old HDDs add up to about 1TB (leftover from previous upgrade project)
6.	Also, many castoff (2GB and 4GB) RAM sticks, not sure they will ever be used again.
7.	A box full of assorted cables, adapters and wires.
8.	Many more old harware not listed here

#### *Dream vs Reality*
I think that most beginners dream of having impressive homelabs with great hardware running great and impressive services. My resources were not that great but I too was determined to build a selfhosted cloud. At a minimum, I would have liked to configure things in such a way that I could run a primary server, secondary server, application server and NAS. 
–	Primary server as my main host on which to run critical VMs and containers. And offcourse this could have been the MacBook Pro (Early 2015), as it is the newest and most powerful.
–	Secondary server, MacBook 2012, as a NAS/Storage Node, attach WD Blue 500GB SSD for fast storage and old HDDs for backups and archives. 
–	Application server, Mac mini (Late 2012), purpose-built for always on services and perhaps lightweight non-critical services.
Alas, the MacBook Pro (Early 2015), is my daily driver, my primary productivity machine and so it cant be the primary server.  Neither can there be a NAS/Storage Node as there are no SATA adapters for the SSD and the old HDDs.
In the end, my homelab was down  to one machine, the MacBook 2012. 

#### *What Next*
Despite this, I went ahead, downloaded the ISO image and installed Proxmox VE on the Macbook 2012. The bare-metal installation process was easy and just like that I had a homelab environment.
The next part was difficult but I managed to build one main service, Nextcloud and make it available to a small group of people. This gave me the opportunity to understand the applications and how self hosting works. There are considerations I need to tackle e.g.  will it be secure, reliable and easily recoverable?

### Conclusion
Self hosting publicly accessible, resource intensive Nextcloud services on a MacBook 2012 is strectching what’s possible. However, to remotely stand a chance of having usable services I decided  to run everything in containers like this.

├─ Proxmox Host (Macbook 2012):
    |- Nginx Proxy Server
    |- Nextcloud as main service
    |- Tailscale Gateway fo remote access
    |- Monitoring
    |_ Backup

In the subsequent posts we are going to look at how I setup Proxmox and all these Linux Containers.

