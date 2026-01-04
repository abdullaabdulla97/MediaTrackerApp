### Build

FROM maven:3.9-eclipse-temurin-17-alpine AS build

# Set working directory inside the container
WORKDIR /app

# Copy Maven files
COPY pom.xml .
COPY src ./src

# Build the Spring Boot application
RUN mvn -q -DskipTests package

### Run

FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

# Copy the built JAR from the build stage
COPY --from=build /app/target/*.jar app.jar

# Expose backend port
EXPOSE 8080

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"] 