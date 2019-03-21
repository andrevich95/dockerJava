FROM maven:3.5.2-jdk-9 AS maven-build
MAINTAINER  Andr Evich
ADD server /usr/src/app
WORKDIR /usr/src/app
RUN mvn clean package

FROM openjdk:9
COPY --from=maven-build /usr/src/app/target/jhttp-*.jar /usr/app/web-server.jar
EXPOSE 8888
ENTRYPOINT ["java","-jar","/usr/app/web-server.jar"]
