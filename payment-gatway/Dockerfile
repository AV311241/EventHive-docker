FROM openjdk:17-jdk-slim

WORKDIR /app

# Copy the built JAR from your local machine into the container
COPY target/*.jar app.jar

# Expose the port your Spring Boot app listens on
EXPOSE 8080

# Run the JAR
ENTRYPOINT ["java", "-jar", "app.jar"]
