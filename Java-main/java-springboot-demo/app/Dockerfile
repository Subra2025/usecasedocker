# Build Stage (Using Maven to build the JAR)
FROM maven:3.8.6-openjdk-11 AS builder
WORKDIR /app
COPY . .
RUN mvn -f pom.xml clean package -DskipTests

# Runtime Stage (Minimal Java environment for execution)
FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar
CMD ["java", "-jar", "app.jar", "--server.port=80"]

