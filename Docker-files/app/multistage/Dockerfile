FROM maven:3.9.12-eclipse-temurin-25-noble AS BUILD_IMAGE
COPY . /app
WORKDIR /app
RUN mvn install

FROM tomcat:10-jdk25

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE /app/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
