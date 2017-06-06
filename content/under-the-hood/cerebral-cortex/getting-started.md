+++
title = "Cerebral Cortex::Getting Started"
description = "Details about the software architecture, design, and developer-oriented interfaces"
keywords = []
+++

In order to start utilizing Cerebral Cortex, some dependencies are necessary to install and configure. Docker containers are utilized to minimize installation efforts both for development and production usage.

# Prerequisites
* Download and install [Docker](https://docs.docker.com/engine/installation/)
* Install [docker-compose](https://docs.docker.com/compose/install/)
* Download [Apache Spark 2.1.x](http://spark.apache.org/downloads.html)
* Clone https://github.com/MD2Korg/CerebralCortex-DockerCompose
* Run `docker-compose up` to initialize the containers before proceeding with the next steps

# Cerebral Cortex codebase
* Clone https://github.com/MD2Korg/CerebralCortex (IntelliJ preferred)
* Follow README.md instructions to configure the project and get everything up and running.

# Data files
Download and extract the zip file from the example data here https://mhealth.md2k.org/datasets/

# Data import
By running the following commands, you can import data into the databases through Cerebral Cortex's methods. This only needs run once for each data set you wish to import and interact with.

```
python3> from cerebralcortex.data_migrator.main import migrate
python3> migrate("/home/ali/IdeaProjects/MD2K_DATA/Site/8be4f601-70ce-3e13-a321-b85ee84b37ce", 64900)
```

# Interacting with data streams
The data diagnostics routines are great examples for exploring Cerebral Cortex's syntax for interacting with data streams

# Running cStress
cStress is the first of many biomarker computations that will be incorporated into the system and this repository will continue to be updated with new capabilities. `cStress.py` provides an example of how we write signal processing code based on the Spark programming abstraction.

For additional details, please visit our [discussion forum](https://discuss.md2k.org/t/getting-started-with-cerebral-cortex/84).
