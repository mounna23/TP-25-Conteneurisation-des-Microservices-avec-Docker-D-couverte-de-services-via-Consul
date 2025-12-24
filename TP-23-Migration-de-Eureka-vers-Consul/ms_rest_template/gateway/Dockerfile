FROM maven:3.8.4-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn -DskipTests clean package

FROM eclipse-temurin:17-jre-jammy
WORKDIR /app
VOLUME /tmp
COPY --from=builder /app/target/*.jar client-service.jar
ENTRYPOINT ["java","-jar","/app/geteway-service.jar"]
