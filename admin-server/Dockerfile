FROM openjdk:11.0
ARG JAR_FILE=build/libs/admin-server-0.0.1-SNAPSHOT.jar
COPY ${JAR_FILE} admin-server.jar
ENTRYPOINT ["java", "-jar", "/admin-server.jar"]
EXPOSE 9003