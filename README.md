# docker-clean


### docker-clean

simple bash script that:
* stops all running containers
* removes all containers
* removes all volumes
* (disabled by deafult) removes all images

```bash
#!/bin/bash
docker ps -a -q | grep -q . && docker stop $(docker ps -a -q) || echo "no containers running"
docker ps -a -q | grep -q . && docker rm $(docker ps -a -q) || echo "no containers present"
docker volume ls -q | grep -q . && docker volume rm $(docker volume ls -q) || echo "no volumes present"
# docker images -q | grep -q . && docker rmi $(docker images -q) || echo "no images present"

```
### install
simple bash script to put a link into /usr/local/bin/

```bash
#!/bin/bash
SCRIPT_DIR=$(cd $(dirname "${BASH_SOURCE[0]}") && pwd)
ln $SCRIPT_DIR/docker-clean /usr/local/bin/
```
