### Build stage
FROM gradle:jdk17-jammy AS BUILD_STAGE
COPY --chown=gradle:gradle . /home/gradle/src
WORKDIR /home/gradle/src
RUN gradle build --no-daemon
#### Package stage
FROM openjdk:17-alpine
MAINTAINER ua.haievskyi
RUN mkdir /app
COPY --from=BUILD_STAGE /home/gradle/src/build/libs/*.jar /app/config-server.jar
ENTRYPOINT ["java","-jar","/app/config-server.jar"]