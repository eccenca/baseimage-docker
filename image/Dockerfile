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

RUN /build/prepare.sh && \
	/build/system_services.sh && \
	/build/utilities.sh && \
	/build/cleanup.sh

CMD ["/sbin/my_init"]
