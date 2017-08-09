FROM liuchong/rustup:all3

MAINTAINER Yann Leretaille <y.leretaille@1aim.com>

WORKDIR /root

RUN apt-get update

# common tools required in automated runners
RUN apt-get install --no-install-recommends -y \
	openssh-client gawk rsync libz-dev
	
# postgresql with extensions
RUN apt-get install --no-install-recommends -y \
	postgresql postgresql-contrib postgis postgresql-*-postgis-* 
	
#clear apt cache
RUN rm -rf /var/lib/apt/lists/*
