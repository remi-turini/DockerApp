FROM maven:3.5-jdk-8-alpine AS builder

WORKDIR /app

COPY pom.xml /app/pom.xml
RUN  mvn dependency:resolve

COPY src /app/src
RUN mvn package

FROM openjdk:8-jre-alpine

COPY --from=builder /app/target/worker-jar-with-dependencies.jar .

CMD java -jar worker-jar-with-dependencies.jar
