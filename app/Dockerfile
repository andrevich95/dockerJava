#compile the app
FROM maven:3.6.0-jdk-11-slim AS maven-build
MAINTAINER  Andr Evich
ADD server /usr/src/app
COPY pom.xml /usr/src/app/pom.xml
WORKDIR /usr/src/app
RUN mvn clean package -DskipTests

#run the app
FROM openjdk:11
COPY --from=maven-build /usr/src/app/target/jhttp-*.jar /usr/app/web-server.jar
EXPOSE 8888
ENTRYPOINT ["java","-jar","/usr/app/web-server.jar"]
