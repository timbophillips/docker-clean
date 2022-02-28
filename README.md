# docker-clean


### docker-clean

simple bash script that:
* stops all running containers
* removes all containers
* removes all volumes
* (disabled by default) removes all images

```bash
#!/bin/bash
docker ps -a -q | grep -q . && docker stop $(docker ps -a -q) || echo "no containers running"
docker ps -a -q | grep -q . && docker rm $(docker ps -a -q) || echo "no containers present"
docker volume ls -q | grep -q . && docker volume rm $(docker volume ls -q) || echo "no volumes present"
# docker images -q | grep -q . && docker rmi $(docker images -q) || echo "no images present"

```
### install
simple bash script to puts links into /usr/local/bin/

```bash
#!/bin/bash
SCRIPT_DIR=$(cd $(dirname "${BASH_SOURCE[0]}") && pwd)
ln $SCRIPT_DIR/docker-clean /usr/local/bin/
ln $SCRIPT_DIR/nuclear-docker-clean /usr/local/bin/
```

### nuclear-docker-clean

nuclear clean out of all docker state files, so use with care

```bash
#!/bin/bash
sudo service docker stop
sudo rm -r /var/lib/docker
sudo service docker start
```
