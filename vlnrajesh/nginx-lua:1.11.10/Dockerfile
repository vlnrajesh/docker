#Base image
FROM centos:7.3.1611

MAINTAINER Rajesh Jonnalagadda "vln.rajesh@students.iiit.ac.in"
LABEL "container_name=nginx-lua"
RUN yum install -q -e 0 -y wget make perl gcc-c++ pcre-devel zlib-devel file && \
    useradd -d  /opt/nginx nginx && \
    mkdir -p /opt/nginx/scripts

ARG NGINX_VERSION=1.11.10
ARG OPENSSL_VERSION=1.0.2f
ARG PCRE_VERSION=8.40
ARG ZLIB_VERSION=1.2.11
ARG LUAJIT_VERSION=2.0.4
ARG NGINX_DEV_KIT_VERSION=v0.3.0
ARG NGINX_LUA_MOD_VERSION=v0.10.7

EXPOSE 80 443

ENV PCRE_VERSION=${PCRE_VERSION} \
    ZLIB_VERSION=${ZLIB_VERSION} \
    OPENSSL_VERSION=${OPENSSL_VERSION} \
    NGINX_VERSION=${NGINX_VERSION} \
    LUAJIT_VERSION=${LUAJIT_VERSION} \
    NGINX_DEV_KIT_VERSION=${NGINX_DEV_KIT_VERSION} \
    NGINX_LUA_MOD_VERSION=${NGINX_LUA_MOD_VERSION} \
    NGINX_SETUP_DIR='/opt/cache/nginx'

ADD setup /opt/nginx/scripts
RUN /opt/nginx/scripts/install.sh
COPY config/nginx.conf /etc/nginx/nginx.conf

VOLUME /usr/share/nginx/html \
       /etc/nginx/conf.d
RUN yum remove -q -e 0 -y wget make perl gcc-c++ pcre-devel zlib-devel file && \
    yum clean all
ENTRYPOINT ["nginx", "-g", "daemon off;"]
