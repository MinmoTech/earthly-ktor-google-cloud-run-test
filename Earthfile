VERSION 0.6
build:
    FROM gradle:7-jdk11
    COPY --chown=gradle:gradle . /home/gradle/src
    WORKDIR /home/gradle/src
    RUN gradle shadowJar --no-daemon
    SAVE ARTIFACT /home/gradle/src/build/libs/*.jar /artifacts/


docker:
    FROM openjdk:11
    EXPOSE 8080:8080
    RUN mkdir /app
    COPY +build/artifacts/*.jar /app/ktor-docker-sample.jar
    ENTRYPOINT ["java","-jar","/app/ktor-docker-sample.jar"]
    SAVE IMAGE ktor-docker-sample:latest


