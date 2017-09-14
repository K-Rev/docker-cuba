### Dockerfile
# App settings on Azure Web App:
# WEBSITES_PORT 8080
# WEBSITES_CONTAINER_START_TIME_LIMIT 600
# WEBSITES_ENABLE_APP_SERVICE_STORAGE true

FROM bitnami/tomcat:8.5

# Tomcat containers files
COPY cuba-container-files/tomcat-users.xml /opt/bitnami/tomcat/conf/
COPY cuba-container-files/context.xml /opt/bitnami/tomcat/conf/
COPY cuba-container-files/logback.xml /opt/cuba_home/
COPY cuba-container-files/persistence.xml /opt/cuba_home/app-core/work/
COPY cuba-container-files/server.xml /opt/bitnami/tomcat/conf/

# Environment
ENV CATALINA_OPTS="-Xmx512m -Dfile.encoding=UTF-8"
ENV CATALINA_OPTS="$CATALINA_OPTS -Dlogback.configurationFile=/opt/cuba_home/logback.xml -Dapp.home=/opt/cuba_home"
ENV CATALINA_OPTS="$CATALINA_OPTS -Dcom.sun.management.jmxremote"
ENV JPDA_OPTS="-Xrunjdwp:transport=dt_socket,address=8787,server=y,suspend=n"
ENV JAVA_OPTS="$JAVA_OPTS -Djava.net.preferIPv4Stack=true -Djava.net.preferIPv4Addresses=true"
ENV TOMCAT_SHUTDOWN_PORT_NUMBER=8005
ENV TOMCAT_HTTP_PORT_NUMBER=8080
ENV TOMCAT_AJP_PORT_NUMBER=8009

# Wars
# COPY wars/app.war /opt/bitnami/tomcat/webapps/
# COPY wars/app-core.war /opt/bitnami/tomcat/webapps/

# Postgres driver
ADD lib/postgresql-9.4.1212.jar /opt/bitnami/tomcat/lib/

# Set up cuba_home share to get logs
RUN ln -s /opt/cuba_home /home/cuba_home

# Expose port 8080 (specify the same port with WEBSITES_PORT app setting)
EXPOSE 8080






