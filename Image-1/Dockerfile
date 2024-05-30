FROM maven:3.8.3-openjdk-17 as build
WORKDIR /app
RUN git clone https://github.com/lahari104/spring-petclinic.git && \
    cd spring-petclinic/ && mvn clean package && cp -r ./target/spring-petclinic-3.2.0-SNAPSHOT.jar /app

FROM openjdk:17-jdk
COPY --from=build /app/spring-petclinic-3.2.0-SNAPSHOT.jar .
EXPOSE 8080
CMD [ "java", "-jar", "./spring-petclinic-3.2.0-SNAPSHOT.jar" ]