# DESCRIPTION: Create a opengl (with glut) container with its dependencies.
# AUTHORS: Felipe Tavares <felmt@hotmail.com>
# USAGE:
#	
#	# Build opengl-glut image
#		docker build -t opengl-glut:1 -f Dockerfile .
#
#	# On windows set DISPLAY var on powershell (change your IP address)
#		set-variable -name DISPLAY -value 192.168.15.89:0.0
#
#	# Run the container and mount the local settings and your code
#		docker create \
#			-it \
#			--privileged \
#			--name opengl-glut \
#			--hostname kagami \
#			--env DISPLAY=$DISPLAY \
#			-v /tmp/.X11-unix:/tmp/.X11.unix \
#			opengl-glut:1
#
# POSSIBLE ISSUES:
#
#	1. Not sure if the necessary packages for X are included on the image.
#
#	2. Commands to get user ip for xserver on linux. (For windows: "ipconfig | grep IPv4 | grep '192.168' | cut -c 40-".)
#

FROM ubuntu:16.04

# System upgrade and basic packages

RUN apt-get update && apt-get -y full-upgrade && \
	apt-get install -y --no-install-recommends \
		build-essential \
		cmake \
		freeglut3-dev \
		git \
		libglm-dev \
		libxmu-dev \
		libxi-dev \
		mesa-utils \
		sudo \
		ssh && \
	apt-get clean
#	&& rm -rf /var/lib/apt/lists/*

# Generate system-wide UTF-8 locale

# RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
#	locale-gen && \
#	echo "LANG=en_US.UTF-8" > /etc/locale.conf

# User setup

RUN useradd -m -s /bin/bash -G sudo suika && \
	passwd -d suika

USER suika

WORKDIR /home/suika

ENV BASH_ENV /home/suika/.profile

CMD /bin/bash
