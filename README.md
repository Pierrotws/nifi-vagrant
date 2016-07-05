# Nifi Vagrant

## Requirements

- Vagrant
- Internet connection

## Get started

just exec 'vagrant up' in this directory
When VM bootstrap and provisionning is finished, go on your host
at http://localhost:8080/

## Configuration

Nifi: version 0.6.1
Port: 8080

If you need a specific version of nifi, edit Vagrantfile and change the
git checkout command line 30.

If port 8080 is not accessible on your host, edit Vagrantfile and change
the port mapping line 8 (..., host: PORT)
 
