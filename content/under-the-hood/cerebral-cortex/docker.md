+++
title = "Cerebral Cortex::Docker"
description = "Details about the software architecture, design, and developer-oriented interfaces"
keywords = []
+++

# Docker
Cerebral Cortex is built for development and production use based on [Docker](https://docker.com/) technologies.


Container customizations and relevant docker-compose files are available in our GitHub [repository](https://github.com/MD2Korg/CerebralCortex-DockerCompose).
This repository contains configurations relevant for both development and production usage.  As support is expanded for other cloud services, the GitHub page
will reflect these additions.

## Installation
Two things must be installed to utilize these Docker containers:

1. [Docker](https://www.docker.com/community-edition)
1. [Docker-compose](https://docs.docker.com/compose/install/)

Once these dependencies have been installed, the commands on this page will function properly.

## Current Containers

<table class="table table-hover">
	<thead>
		<th>Name</th>
    <th>Container</th>
    <th>Description</th>
	</thead>
	<tbody>
		<tr>
			<th scope="row">NGINX</th>
			<td>Custom: nginx</td>
      <td>Frontend web proxy for accessing services and providing TLS encryption</td>
		</tr>
    <tr>
			<th scope="row">FluentD</th>
			<td>Custom: fluentd</td>
      <td>Open source data collector for unified logging layer</td>
		</tr>
    <tr>
      <th scope="row">Elastic search</th>
      <td>elasticsearch</td>
      <td>A distributed, RESTful search and analytics engine</td>
    </tr>
    <tr>
      <th scope="row">Kibana</th>
      <td>kibana</td>
      <td>Visualize your Elasticsearch data and navigate the Elastic Stack</td>
    </tr>
    <tr>
      <th scope="row">Grafana</th>
      <td>grafana/grafana</td>
      <td>Time-series visualization tool for Cerebral Cortex datastreams</td>
    </tr>
    <tr>
      <th scope="row">InfluxDB</th>
      <td>influxdb:1.2</td>
      <td>Time-series database designed for IoT monitoring and used by Grafana</td>
    </tr>
    <tr>
      <th scope="row">Jupyter Notebook</th>
      <td>Custom: md2k-spark-notebook</td>
      <td>Jupyter Spark Python3 notebook for providing a web based UI into Cerebral Cortex</td>
    </tr>
    <tr>
      <th scope="row">Kafka</th>
      <td>wurstmeister/kafka</td>
      <td>Apache Kafka is a distributed streaming platform used by Cerebral Cortex for handing data ingestion and routing</td>
    </tr>
    <tr>
      <th scope="row">ZooKeeper</th>
      <td>wurstmeister/zookeeper</td>
      <td>ZooKeeper is a distributed, open-source coordination service for distributed applications and used by Kafka</td>
    </tr>
    <tr>
      <th scope="row">Cassandra</th>
      <td>Custom: cassandra:3.9</td>
      <td>A distributed NoSQL database management system designed to handle large amounts of data across many commodity servers</td>
    </tr>
    <tr>
      <th scope="row">MySQL</th>
      <td>mysql:5.7</td>
      <td>A relational database management system</td>
    </tr>
  </tbody>
</table>


# Development
Cerebral Cortex can be run for development purposes by cloning this [repository](https://github.com/MD2Korg/CerebralCortex-DockerCompose) and launching docker-compose.
A machine with at least 16GB of memory is recommended to run all the containers.

```
> git clone https://github.com/MD2Korg/CerebralCortex-DockerCompose
> cd CerebralCortex-DockerCompose
> docker-compose up
```
This will tell Docker to download all dependencies and build the necessary local images before starting all the containers on your system.
Once the system has started everything up, you can access Cerebral Cortex's capabilities with these [instructions](/under-the-hood/cerebral-cortex/working-with-cerebral-cortex)

# Production
