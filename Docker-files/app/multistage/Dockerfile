FROM maven:3.9.9-eclipse-temurin-21-jammy AS build_image
RUN git clone https://github.com/hponemahn/vprofile-project-proton.git
WORKDIR /vprofile-project-proton
RUN git checkout docker && mvn install

FROM tomcat:10-jdk21

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=build_image vprofile-project-proton/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
