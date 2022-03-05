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
REPO_DIR=$(cd $(dirname "${BASH_SOURCE[0]}") && pwd)
ln -sf $REPO_DIR/scripts/* /usr/local/bin/
```

### nuclear-docker-clean

nuclear clean out of all docker state files, so use with care

```bash
#!/bin/bash
sudo service docker stop
sudo rm -r /var/lib/docker
sudo service docker start
```

### upgrade-apt-and-node

shorthand for upgrading packages in ubuntu

```bash
#!/bin/bash
sudo apt update
sudo apt -yy dist-upgrade
sudo apt -yy autoremove
```

### node-repo-refresh

shorthand for refreshing repo from remote
(useful when using multiple computers)

```bash
#!/bin/bash
rm -r node_modules
git pull
npm install
```