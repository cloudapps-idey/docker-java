# For Java 8, try this
# FROM openjdk:8-jdk-alpine

FROM maven:3.8.5-openjdk-11 AS maven_build

COPY pom.xml /tmp/

COPY src /tmp/src/

WORKDIR /tmp

RUN mvn package

# For Java 11, try this
#FROM adoptopenjdk/openjdk11:alpine-jre

FROM registry.redhat.io/ubi8/openjdk-11

# Refer to Maven build -> finalName
ARG JAR_FILE=data/spring-boot-web.jar

# cd /opt/app
#WORKDIR /opt/app

# cp target/spring-boot-web.jar /opt/app/app.jar
COPY ${JAR_FILE} app.jar

# java -jar /opt/app/app.jar
ENTRYPOINT ["java","-jar","app.jar"]

## sudo docker run -p 8080:8080 -t docker-spring-boot:1.0
## sudo docker run -p 80:8080 -t docker-spring-boot:1.0
## sudo docker run -p 443:8443 -t docker-spring-boot:1.0