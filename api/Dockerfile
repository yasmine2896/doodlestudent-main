# Stage : BUILD
FROM openjdk:11 as build
WORKDIR /app
COPY mvnw .
COPY .mvn .mvn
COPY pom.xml .
COPY src src
RUN ./mvnw clean package -Dquarkus.package.type=uber-jar -DskipTests

# Stage : run
FROM openjdk:11
COPY --from=build /app/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar /app/lib/api.jar
RUN ls /app/lib
ENTRYPOINT ["java","-jar","/app/lib/api.jar"]
