FROM maven:3.9-eclipse-temurin-8 as builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

FROM eclipse-temurin:8-jre
LABEL maintainer="joffrey mischler<jmischler72>"

WORKDIR /app

COPY --from=builder /app/target/java-*.jar java-app.jar

CMD ["java", "-jar", "java-app.jar"]

EXPOSE 8448