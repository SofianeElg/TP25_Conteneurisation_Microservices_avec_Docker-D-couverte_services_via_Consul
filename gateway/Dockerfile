FROM maven:3.8.4-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn -DskipTests clean package

FROM eclipse-temurin:17-jre-jammy
WORKDIR /app
VOLUME /tmp
COPY --from=builder /app/target/*.jar gateway-service.jar
ENTRYPOINT ["java","-jar","gateway-service.jar"]
