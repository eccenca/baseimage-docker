####
#
# Dockerfile for building an baseimage as base for further images;
#
# this is a fork from https://github.com/phusion/baseimage-docker 
####

FROM ubuntu:14.04
MAINTAINER Henri Knochenhauer <henri.knochenhauer@eccenca.com>
MAINTAINER René Pietzsch <rene.pietzsch@eccenca.com>

ENV HOME /root
RUN mkdir /build
ADD . /build
# Set the time zone
RUN echo "Europe/London" > /etc/timezone && dpkg-reconfigure -f noninteractive tzdata \
 && cp /etc/timezone /tz/ && cp /etc/localtime /tz/

RUN /build/prepare.sh && \
	/build/system_services.sh && \
	/build/utilities.sh && \
	/build/cleanup.sh

# http://jaredmarkell.com/docker-and-locales/
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

CMD ["/sbin/my_init"]
