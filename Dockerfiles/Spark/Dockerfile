FROM ubuntu:16.04

# install java
RUN apt-get update
RUN apt-get install -y openjdk-8-jre
RUN apt-get install dos2unix

# copy entrypoint 
COPY entrypoint.sh /
RUN dos2unix /entrypoint.sh
RUN chmod u+x /entrypoint.sh

# copy spark jar on docker and set permissions
RUN mkdir -p /jarFiles
COPY SparkConsumer.jar /jarFiles
RUN chmod u+x /jarFiles/SparkConsumer.jar

# install spark
ADD http://www-eu.apache.org/dist/spark/spark-2.0.1/spark-2.0.1-bin-hadoop2.7.tgz /spark.tgz
RUN tar -xzf /spark.tgz && mv /spark-2.0.1-bin-hadoop2.7 /spark

# expose spark
EXPOSE 8080
EXPOSE 7077

ENTRYPOINT /entrypoint.sh