FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone  https://github.com/anselem-okeke/container-project.git
RUN cd container-project && git checkout docker && maven install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Anselem"
RUN rm-rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE container-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]