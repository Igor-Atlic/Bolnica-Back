#
# Build stage
#
FROM maven:3.6.0-jdk-11-slim AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package -DskipTests


#
# Package stage
#
FROM openjdk:11

LABEL org.opencontainers.image.source https://github.com/RAF-SI-2021/Bolnica-Back

COPY --from=build /home/app/target/user-0.0.1-SNAPSHOT.jar /usr/local/lib/user.jar
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "/usr/local/lib/user.jar"]