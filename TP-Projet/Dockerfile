# Dockerfile for Spring Boot app
FROM openjdk:17-jdk-slim
COPY target/*.jar app.jar
EXPOSE 8083
ENTRYPOINT ["java", "-jar", "/app.jar"]
