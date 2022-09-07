FROM gradle:7.2.0-jdk17 AS build
COPY --chown=gradle:gradle ./demo/ /home/gradle/src
WORKDIR /home/gradle/src
RUN gradle build --no-daemon 

FROM openjdk:17
EXPOSE 8080
WORKDIR /app
COPY --from=build /home/gradle/src/build/libs/d*.jar ./spring-boot-application.jar
ENTRYPOINT ["java", "-jar", "spring-boot-application.jar"]