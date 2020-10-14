FROM openjdk:11.0
ARG JAR_FILE=build/libs/client-service-0.0.1-SNAPSHOT.jar
COPY ${JAR_FILE} client-service.jar
ENTRYPOINT ["java", "-jar", "/client-service.jar"]
EXPOSE 8080