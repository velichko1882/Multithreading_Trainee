FROM ubuntu:18.04

MAINTAINER Valentin Velichko <velichko1880@gmail.com>

RUN apt-get update
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y maven

ADD Task5 .

RUN cd TravelManager/

RUN mvn package

CMD ["java", "-cp", "./TravelManager/target/classes/", "by.epamlab.Runner"]
