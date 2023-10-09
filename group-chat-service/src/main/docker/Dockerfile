FROM maven:3.8.3-jdk-8-slim AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package

FROM ubuntu:20.04

RUN apt-get update && \
    apt-get -y install default-jre


FROM openjdk:8-jre-alpine
COPY --from=build /home/app/target/groupchat-0.1.0.jar /usr/local/lib/groupchat-0.1.0.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/groupchat-0.1.0.jar"]

