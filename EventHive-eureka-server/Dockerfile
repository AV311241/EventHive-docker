# ----------- Stage 1: Build the application -----------

# Use Maven with JDK for building
FROM maven:3.9.6-eclipse-temurin-17 AS build

# Set working directory inside container
WORKDIR /app

# Copy Maven project files
COPY pom.xml .
COPY src ./src

# Package the application
RUN mvn dependency:go-offline
RUN mvn clean package -DskipTests

# ----------- Stage 2: Run the application -----------

# Use a lightweight JDK image to run the app
FROM eclipse-temurin:17-jdk-alpine

# Set working directory
WORKDIR /app

# Copy built JAR from previous stage
COPY --from=build /app/target/*.jar app.jar

# Expose application port
EXPOSE 8080

# Run the Spring Boot app
ENTRYPOINT ["java", "-jar", "app.jar"]
