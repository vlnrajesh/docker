Image Name
===========
nginx-lua

Description
============
A full-fledged web platform that integrates the standard Nginx core, LuaJIT.
It also includes high quality 3rd-party Nginx modules and their external dependencies.
It is designed to help Team-4 easily build scalable web applications, web services, and dynamic web gateways.
This images can be used as LB and Router in our final project.

Image tags
=========
vlnrajesh/nginx-lua:1.11.10
vlnrajesh/nginx-lua:default-site

nginx-lua:1.11.10
=================
* Image is build for install and setup nginx with Lua scripts. 
* Build can accept dynamic parameters during run time avoiding to update Dockerfile dynamically 
* Build can be independently used by  removing comments at ENTRYPOINT line# 37
* Image is security enhanced and removed default site and configurations for security issues
* Image also configured not to expose System information to end use and removed all header tags
* Image also consists metadata for enabled dynamic scaling

nginx-lua:default-site
=======================
* Image build based on vlnrajesh/nginx-lua:1.11.10
* Adds default-site/html and configuration files


Build Instructions:
===================

vlnrajesh/nginx-lua:1.11.10
---------------------------
1. Download and extract zip file and visit vlnrajesh/nginx-lua:1.11.10 directory
2. docker build -t [REPOSITORY/]<IMAGE_NAME>:[TAG_NAME] .
   Please note that REPOSITORY and TAG_NAME are optional
3. Remove Line #37 and rebuild if you want to run as an independent container

vlnrajesh/nginx-lua:default-site
---------------------------
1. Download and extract zip file and visit vlnrajesh/nginx-lua:default-site directory
2. docker build -t [REPOSITORY/]<IMAGE_NAME>:[TAG_NAME] .
   Please note that REPOSITORY and TAG_NAME are optional
3. Entrypoint is defined to start the container, you can overwrite entrypoint to override with any additional commands



RUN Instructions
================
vlnrajesh/nginx-lua:default-site
--------------------------------
1.  docker pull vlnrajesh/nginx-lua:default-site
2.  docker run -td --name nginx-lua -p 8080:80 vlnrajesh/nginx-lua:default-site
3.  docker stop nginx-lua to stop the container
4. 	docker start nginx-lua to start the container from its previous state
5. 	docker rm nginx-lua to remove container from the host.

vlnrajesh/nginx-lua:1.11.10
---------------------------
Above instructions holds good with this image, except
1. Make entrypoint available
2. Mount default-site html and configuration point along with above options.


