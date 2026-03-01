# Stage 1 — Build the application
FROM maven:3.9.9-eclipse-temurin-11 AS builder

WORKDIR /build

# copy everything
COPY . .

# compile and create jar
RUN mvn clean package -DskipTests


# Stage 2 — Run the application
FROM eclipse-temurin:11

WORKDIR /app

# copy jar from builder stage
COPY --from=builder /build/target/*.jar app.jar

EXPOSE 8081

ENTRYPOINT ["java","-jar","app.jar"]