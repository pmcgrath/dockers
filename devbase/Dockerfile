# Base image for development - Based on ubuntu:latest, installs common tools that will be used by all dev images\containers
# Build using: docker build -t pmcgrath/base .
FROM ubuntu:latest

# Created by and at
MAINTAINER pmcgrath "pmcgrath@gmail.com"
ENV REFRESHED_AT 2015-08-15

# Add first group and user to make sure their IDs get assigned consistently, regardless of whatever dependencies get added later
RUN 	groupadd -r pmcgrath && useradd -r -g pmcgrath pmcgrath

# Install base s/w
# Set the env variable DEBIAN_FRONTEND to noninteractive
ENV 	DEBIAN_FRONTEND noninteractive
# To install the latest git we need to use a ppa and rather then using add-apt-repository which has bunch of dependcies we will do so manually
# 	See 
#		https://launchpad.net/~git-core/+archive/ubuntu/ppa
#	 	http://askubuntu.com/questions/38021/how-to-add-a-ppa-on-a-server
#	First 3 commands take care of the git-core ppa
RUN	echo "deb http://ppa.launchpad.net/git-core/ppa/ubuntu $(lsb_release -cs) main" >> /etc/apt/sources.list && \
	echo "deb-src http://ppa.launchpad.net/git-core/ppa/ubuntu $(lsb_release -cs) main" >> /etc/apt/sources.list && \
        apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E1DF1F24 && \
	apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install -y curl git tmux vim wget && \
	rm -rf /var/lib/apt/lists/*

