# Stage 1: Build with Maven
FROM maven:3.9.5-eclipse-temurin-17 AS build
WORKDIR /app
# 1. Copy only pom.xml to download dependencies (cached layer)
COPY pom.xml .
RUN mvn dependency:go-offline

# 2. Copy source and build
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Run the application with JRE
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
# Copy the JAR file from the build stage (adjust 'app-name-1.0.0.jar' to your file name)
COPY --from=build /app/target/voting-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]