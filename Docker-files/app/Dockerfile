FROM openjdk:11 AS BUILD_IMAGE
RUN apt-get update -y && apt-get install maven -y
RUN git clone https://github.com/devopshydclub/vprofile-project.git
RUN cd vprofile-project && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh","run"]
