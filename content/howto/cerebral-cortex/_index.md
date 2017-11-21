+++
title = "How-To: Cerebral Cortex Setup"
description = "Details about the using Cerebral Cortex"
keywords = []
+++

# Contents

 - [Requirements](#req)
 - [Installation Instructions](#install)
 - [Expected performance](#perform)


## <a name="req"></a>Requirements
Linux node(s) running CentOS 7.2+


## <a name="install"></a>Installation Instructions
Install CentOS 7.2 on all systems

Install mysql on the head node

Create a dedicated user and associated password

Install influxdb on the head node

Install cassandra on all nodes

Modify the configuration to tell Cassandra to utilize appropriate storage mounts

Increase cassandra batch_size_fail_threshold_in_kb: to 1024 and batch-size_warn_threshold_in_kb: to 512

Install Apache Spark 2.2.0 on all nodes

Configuration spark to run as as a standalone cluster

Export share RAID array from head node to worker nodes as /cerebralcortex

Install Docker on head node

Configure firewall to allow flexible Docker container communications (See docker-compose.yml)

Docker images

Clone

CerebralCortex-DockerCompose

CerebralCortex-APIServer

CerebralCortex-KafkaSparkStreaming

## <a name="perform"></a>Expected Performance
