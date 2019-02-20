FROM ubuntu:16.04

MAINTAINER Eflyax

RUN DEBIAN_FRONTEND=noninteractive

ENV LANGUAGE=C.UTF-8
ENV LC_ALL=C.UTF-8
ENV LC_CTYPE=UTF-8
ENV LANG=C.UTF-8
ENV TERM xterm

RUN apt-get update && \
	apt-get install -y software-properties-common

USER root
RUN apt-get clean && \
	rm -rfv \
	/tmp/* \
	/var/lib/apt/lists/* \
	/var/tmp/*
