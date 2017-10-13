# docker-cuba
Cuba Platform Docker image on Bitnami Tomcat for Microsoft Azure

## Description
The image doesn't actually contains the Cuba Platform. It is a pre-configured Tomcat instance to be deployed on Azure Web App service as a custom docker image.

### Personalization
Build one or two wars setting "Application home directory" to /opt/cuba_home.
Use as a base and copy your WAR(s) to /opt/bitnami/tomcat/webapps/ (in the Dockerfile).
Copy your persistence.xml to cuba-container-files.
It is configured to use postgresql-9.4.1212.jar: put the corresponding file from your Tomcat local deploy to the lib directory before building the image. If needed, copy other jdbc drivers to /opt/bitnami/tomcat/lib/ (in the Dockerfile).

## To run the container
cd 'cuba-version' &&
docker build -t cuba . &&
docker run -d -p 80:8080 cuba &&
