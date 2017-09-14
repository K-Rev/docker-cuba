# docker-cuba
Cuba Platform Docker image on Bitnami Tomcat for Microsoft Azure

## Description
The image doesn't actually contains the Cuba Platform. It is a pre-configured Tomcat instance to be deployed on Azure Web App service as a custom docker image. Use as a base and copy your WAR(s) to /opt/bitnami/tomcat/webapps/.
It uses Postgres as database. If needed, copy jdbc drivers to /opt/bitnami/tomcat/lib/.

## To run the container
docker run -p 80:8080 gmlion/cuba
