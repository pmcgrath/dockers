# Pending
# Sort out docker group membership so we do not need to use sudo everywhere ?

# Remove all containers - even running ones
docker ps -q -a | xargs docker rm

# Remove all docker images starting with pmcg
docker images | grep "^pmcg" | awk '{print $3}' | xargs docker rmi



