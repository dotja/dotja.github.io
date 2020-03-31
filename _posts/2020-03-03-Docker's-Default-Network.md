---
layout: post
date: 2020-03-03
summary: "A look into Docker's bridge network."
content_description: "Docker has a default bridge network. A basic explanation about Docker's bridge network and how containers can interact if they are on the same network."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Docker's Default Network</span></h1>
    <small>03 Mar 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>For</kbd> a new device to interact with your computer it needs the help of a driver. The driver is a software that can act as an interface between the new device and your computer. 
</p>

<p id="blog_text">
Drivers for commonly used devices such as a mouse usually come with the operating system.
When you buy a new graphical tablet for instance, the first thing you usually do before using it is install the device driver which you can download online from the manufacturer's website. This allows the graphical tablet to communicate and interact with your operating system.
</p>

<p id="blog_text">
A networking device or a network adapter such as wireless cards or ethernet cards are used to allow the computer to connect to the internet. A network driver in this case is needed to handle the data received from the internet using an internet protocol.
</p>

<p id="blog_text">
When you install Docker, you get a client and a daemon. You use Docker commands such as run and build to interact with the client which in turn communicates with the daemon that does the heavy work.
</p>

<p id="blog_text">
The Docker daemon creates docker0 which is a virtual network interface described as the bridge network that has a bridge driver. It randomly chooses an avialable IP address and assigns it to docker0.
</p>

<pre>
## on your host
## view the docker networks
docker network ls

## view docker0
ifconfig docker0

## you can inspect the bridge network and view the connected containers
docker network inspect bridge
</pre>

<p id="blog_text">
If a network is not specified, containers by default join the bridge network and are able to communicate with each others.
</p>

<pre>
## running a container
docker run -d --name my_container my_image_id

## is equivalent to
docker run -d --net=bridge --name my_container my_image_id
</pre>

<p id="blog_text">
When running 2 containers, exec into 1 and ping the other container to check that they are able to communicate.
</p>

<pre>
## You can view the IP address using
hostname -I

## or
ifconfig

## inside the container install ifconfig
sudo apt install net-tools

## inside the container install ping
sudo apt install iputils-ping

## after finding the IP addresses
## inside container 1
ping container2_ip
</pre>

<p id="blog_text">
By default, traffic from the container is NOT forwarded to the outside host. Therefore the ports of the container where an app is running must be published against the host's ports.
</p>

<p id="blog_text">
Users are able to create their own network but many times you would want to configure the default bridge network instead. You can simply specify your settings such as IP address and netmask of docker0 in /etc/docker/daemon.json which gets read by docker on installation or restart.
</p>
</div>