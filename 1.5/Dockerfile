FROM ubuntu:14.04

ENV HAPROXY_MAJOR 1.5
ENV HAPROXY_VERSION 1.5.11
ENV HAPROXY_MD5 5500a79d0d2b238d4a1e9749bd0c2cb2

# install confd
RUN apt-get update && apt-get install -y wget
RUN wget --no-check-certificate https://github.com/kelseyhightower/confd/releases/download/v0.11.0/confd-0.11.0-linux-amd64
RUN mv confd-0.11.0-linux-amd64 /usr/local/bin
RUN mv /usr/local/bin/confd-0.11.0-linux-amd64 /usr/local/bin/confd
RUN chmod +x /usr/local/bin/confd

# install haproxy
RUN apt-get install -y software-properties-common
RUN apt-get install -y python-software-properties
RUN add-apt-repository ppa:vbernat/haproxy-1.5
RUN apt-get update && apt-get install -y haproxy

# install curl
RUN apt-get update &&apt-get install -y curl

RUN mkdir -p /etc/confd/conf.d
RUN mkdir -p /etc/confd/templates
ADD confd/haproxy.toml /etc/confd/conf.d
ADD confd/haproxy.cfg.tmpl /etc/confd/templates
