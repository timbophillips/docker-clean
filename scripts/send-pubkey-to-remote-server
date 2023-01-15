#!/bin/bash

# script to (generate and) send public key to remote server to allow
# password free ssh access
# it requires a ~/.ssh directory to exist on the remote server

#variables
remote_uname=$1
remote_IP=$2
port=$3

# move to the home dir
cd ~/

#if no keys, make them
if [ ! .ssh/id_rsa.pub ]; then ssh-keygen ; fi 

# get authorized_keys file frome remote server
# if there aren't any it generates an error but thats fine
scp -P$port $remote_uname@$remote_IP:~/.ssh/authorized_keys ./authorized_keys-remote_server

# put local public key into the list of remote server auth keys
# if the file doesn't exist this creates it
cat ~/.ssh/id_rsa.pub >>authorized_keys-remote_server

# send it on back to the remote server
scp -P$port ./authorized_keys-remote_server $remote_uname@$remote_IP:~/.ssh/authorized_keys 

# clean up
rm ./authorized_keys-remote_server



