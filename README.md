# DevOps Playground #2 - ELK Stack
This is the accompanying repo to DevOps Playground #2.

## Aim
The aim of this playground is to:
* Teach you a little about the [ELK](https://www.elastic.co/webinars/introduction-elk-stack) stack
* Parse some fake Apache webserver logs with Logstash and send them to Elasticsearch
* Create dashboards from the data using Kibana and alalyse some of the data.

## Included Components
You will notice a [Vagrantfile](Vagrantfile) and a [docker-compose](docker-compose.yml) file in the repository.

The [Vagrantfile](Vagrantfile) is provided for users who don't have docker installed on their laptop or don't want to install it. You can use the vagrant vm - or run the stack using [docker-compose](https://docs.docker.com/compose/). Upto you!

To run the [docker-compose](docker-compose.yml) file without the Vagrant VM - you will need

**Note:** We will also distribute a VM  image with all the required components at the labs if you haven't managed to get vagrant or docker working.


## Running the Components
To start the vm with vagrant:
```shell
# cd into the location where you cloned this repo.
$ cd /path/where/i/cloned/this/repo

# Run the vagrant box
$ vagrant up

# SSH onto the box
$ vagrant ssh
```

To do this you will need to have installed both [Vagrant](https://www.vagrantup.com/docs/installation/) and [Virtualbox](https://www.virtualbox.org/wiki/Downloads)

To start the docker-compose environment:
```shell
# cd into the location where you cloned this repo.
$ cd /path/where/i/cloned/this/repo

# Ensure all images are built
$ docker-compose build

# Run the environment
$ docker-compose run
```

## Accessing the Components
* **kibana:** http://localhost:5601
* **elasticsearch:** http://localhost:9200
* **logstash:** http://localhost:5044

## Log generation
To generate the 

## Logsender configuration
To forward the logs from the fake webserver container to the logstash container for processing, [file-beat](https://www.elastic.co/products/beats/filebeat) is used.

Filebeat is part of the beats family and is intended to replace tools like syslog, rsyslog and logstash forwarder. It's very lightweight and written in the golanguage so is also cross platform.

Let's pick apart the [configuration file](fake-webserver/filebeat.yml) a little:

The first section defines some prospectors, which are essentially paths to match for logfiles.

## References
* https://docs.docker.com/compose/compose-file/
* https://hub.docker.com/_/logstash/
* https://hub.docker.com/_/kibana/
* https://hub.docker.com/_/elasticsearch/
* https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-configuration-details.html#configuration-filebeat-options
* https://www.elastic.co/guide/en/logstash/current/configuration.html
* https://www.elastic.co/guide/en/logstash/current/config-examples.html
* https://www.elastic.co/guide/en/logstash/current/plugins-inputs-beats.html
