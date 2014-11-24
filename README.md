# Spark in docker
Example on running spark on your mac (some parts below might differ for non-macs, e.g. the need of using 'sudo' in front of everything), without too much work.

*This works*

**boot2docker.app**

**docker pull sequenceiq/spark:1.1.0**

**docker run -it --net=host sequenceiq/spark:latest /etc/bootstrap.sh -bash**
*This is the way to get the application to use the default ports as it should!*

**boot2docker ip**
*Tells you the localhost ip used by docker, let's call it '<'docker ip'>' here.* 

*What's up?*
**http://<docker ip>:50070**
**http://<docker ip>:8088**

*In the container, do* **/usr/local/spark/sbin/start-all.sh**
*Now look at* **http://<docker ip>:8080**

*In the container, do* **/usr/local/spark/bin/spark-shell**
*Now look at* **http://<docker ip>:4040**

*Call spark from outside (really cool):*

**bash-3.2$ docker run sequenceiq/spark /usr/local/spark/bin/spark-submit --class org.apache.spark.examples.SparkPi --master local --driver-memory 1g --executor-memory 1g --executor-cores 1 /usr/local/spark/lib/spark-examples-1.1.0-hadoop2.4.0.jar**
