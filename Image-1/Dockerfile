FROM maven:3.8.3-openjdk-17 as build
ARG GITLAB_PAT=""
WORKDIR /app
RUN git clone https://venkatajntuk:${GITLAB_PAT}@gitlab.insigniaconsultancy.com/venkatajntuk/gitlab-private-project.git && \
    cd gitlab-private-project/ && mvn clean package && cp -r ./target/spring-petclinic-3.2.0-SNAPSHOT.jar /app

FROM openjdk:17-jdk
COPY --from=build /app/spring-petclinic-3.2.0-SNAPSHOT.jar .
EXPOSE 8080
CMD [ "java", "-jar", "./spring-petclinic-3.2.0-SNAPSHOT.jar" ]