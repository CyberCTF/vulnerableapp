# VulnerableApp ships no Dockerfile for the application itself: upstream builds the image with
# Jib (`./gradlew jibDockerBuild`) on top of its base image (app/Dockerfile.base:
# eclipse-temurin:17-jre plus ping). This Dockerfile does the same from the vendored source:
# Gradle 8.5 (the wrapper's version) builds the Spring Boot jar, which runs on that same base,
# with the scanner ground-truth folder at /scanner as Jib places it.
FROM gradle:8.5-jdk17 AS build
COPY app/ /src
WORKDIR /src
RUN gradle bootJar --no-daemon -x test

FROM eclipse-temurin:17-jre
RUN apt-get update && \
    apt-get install -y iputils-ping && \
    rm -rf /var/lib/apt/lists/*
COPY --from=build /src/build/libs/VulnerableApp-1.0.0.jar /app/VulnerableApp.jar
COPY app/scanner /scanner
WORKDIR /
EXPOSE 9090
CMD ["java", "-jar", "/app/VulnerableApp.jar"]
