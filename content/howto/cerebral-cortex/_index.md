+++
title = "How-To: Cerebral Cortex Setup"
description = "Details about the using Cerebral Cortex"
keywords = []
+++

# Contents

 - [Requirements](#req)
 - [Installation Instructions](#install)
 - [Expected performance](#perform)

## Option 1: Virtual machine

* Download and install [Virtual Box](https://www.virtualbox.org/wiki/Downloads)
* Download the Cerebral Cortex virtual machine image: [here](http://)

The virtual machine exposes port 80/443 to the outside world you will need your
machines IP address or dns name before proceeding


### Accounts and Passwords
* root/cerebralcortex
* cerebralcortex/md2k

## <a name="req"></a>Requirements
* Linux platform (CentOS 7.2+ or Ubuntu 17.04+)

## <a name="install"></a>Testing out Cerebral Cortex

### Docker
* Install [Docker](https://docs.docker.com/engine/installation/) and
[Docker-Compose](https://docs.docker.com/compose/install/)


### Code Repositories
Create a folder `cerebralcortex` in you user directory and clone the following repositories into it

```
git clone https://github.com/MD2Korg/CerebralCortex-DockerCompose
git clone https://github.com/MD2Korg/CerebralCortex-2.0
git clone https://github.com/MD2Korg/CerebralCortex-APIServer
```

### Modifying the configuration for your machines
Docker-Compose does not provide a good way to abstract away the configuration of
IP addresses and the files must be modified based on your machine.

* foo
* bar
* ...


### Building Docker Images
Docker will download and build a number of images that Cerebral Cortex leverages.  To do this:

```
cd CerebralCortex-DockerCompose
docker-compose pull
docker-compose build
```

Once this process completes, all the containers are ready to go for testing the system.

### Running a Docker-based system
To startup Cerebral Cortex and see all the system logs.
```
docker-compose up
```

If you want to run the system in the background so that you can logout of a session or terminal.
```
docker-compose up -d
```

and to see the logs as necessary
```
docker-compose logs -f

...
SOMETHING HERE
...
```

### Ensuring Cerebral Cortex is functional

```
docker-compose ps

Name                    Command               State                                      Ports
---------------------------------------------------------------------------------------------------------------------------------------
md2k-api-server   /entrypoint.sh /usr/bin/su ...   Up      443/tcp, 80/tcp
md2k-cassandra    /bootstrap.sh cassandra -f       Up      7000/tcp, 7001/tcp, 7199/tcp, 0.0.0.0:9042->9042/tcp, 0.0.0.0:9160->9160/tcp
md2k-grafana      /run.sh                          Up      0.0.0.0:3000->3000/tcp
md2k-influxdb     /entrypoint.sh influxd           Up      0.0.0.0:8086->8086/tcp
md2k-jupyterhub   jupyterhub --no-ssl --conf ...   Up
md2k-kafka        start-kafka.sh                   Up      0.0.0.0:9092->9092/tcp
md2k-minio        /usr/bin/docker-entrypoint ...   Up      0.0.0.0:9000->9000/tcp
md2k-mysql        docker-entrypoint.sh mysqld      Up      0.0.0.0:3306->3306/tcp
md2k-nginx        nginx -g daemon off;             Up      0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
md2k-zookeeper    /bin/sh -c /usr/sbin/sshd  ...   Up      0.0.0.0:2181->2181/tcp, 22/tcp, 2888/tcp, 3888/tcp
```
This command shows the status of the currently running containers and how each
exposes ports, which are configured for a develoment and testing setup and not
production enviornments.




## <a name="perform"></a>Expected Performance
