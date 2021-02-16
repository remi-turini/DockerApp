FROM maven:3.5-jdk-8-alpine AS builder

COPY pom.xml /tmp/
COPY src /tmp/src/
WORKDIR /tmp/

RUN mvn -B -f /tmp/pom.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve
RUN mvn package


FROM openjdk:8-jre-alpine

RUN java -jar /tmp/worker-jar-with-dependencies.jar
