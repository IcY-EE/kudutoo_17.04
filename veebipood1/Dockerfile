FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /app

# Kopeeri pom.xml (see asub samas kaustas kus Dockerfile)
COPY pom.xml .

# Kopeeri src kaust (see asub samas kaustas kus Dockerfile)
COPY src ./src

# Ehita projekt
RUN mvn clean package -DskipTests

# Teine etapp (Runtime)
FROM eclipse-temurin:21-jre
WORKDIR /app

# Kopeeri ehitatud JAR fail
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]