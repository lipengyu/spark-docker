spark-docker
============

Example on running spark on your mac, without too much work


# Spark in docker

This works

boot2docker.app

docker pull sequenceiq/spark:1.1.0

docker run -it --net=host sequenceiq/spark:latest /etc/bootstrap.sh -bash

This is the way to get the application to use the default ports as it should!

boot2docker ip

Tells you the localhost ip used by docker

Whats up?
http://192.168.59.103:50070
http://192.168.59.103:8088

In the container, do /usr/local/spark/sbin/start-all.sh
Now look at http://192.168.59.103:8080

In the container, do /usr/local/spark/bin/spark-shell
Now look at http://192.168.59.103:4040

Call spark from outside (really cool):

bash-3.2$ docker run sequenceiq/spark /usr/local/spark/bin/spark-submit --class org.apache.spark.examples.SparkPi --master local --driver-memory 1g --executor-memory 1g --executor-cores 1 /usr/local/spark/lib/spark-examples-1.1.0-hadoop2.4.0.jar
