FROM maven:3.8.5-openjdk-11 AS build

WORKDIR /app

COPY . .

RUN mvn -f eureka-service/pom.xml clean package -DskipTests

FROM openjdk:11-jre-slim

WORKDIR /app

COPY --from=build /app/eureka-service/target/*.jar app.jar

EXPOSE 8761

ENTRYPOINT ["java", "-jar", "app.jar"]

