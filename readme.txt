# Remove all containers - even running ones
docker ps -q -a | xargs docker rm

# Remove all docker images starting with pmcg
docker images | grep "^pmcg" | awk '{print $3}' | xargs docker rmi

# Docker files
## devbase
Base image for dev images
Is based on ubuntu:latest which is 14.04.3 at the time the dockerfile was created
Includes the following
- curl 
- git
- tmux
- vim
- wget


## graphite
Based on graphite in late 2014 - this could be out of date as I have not used this lately

