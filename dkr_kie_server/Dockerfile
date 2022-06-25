# Dockerfile

FROM jboss/kie-server-showcase:latest

RUN rm /opt/jboss/.m2/settings.xml
COPY settings.xml /opt/jboss/.m2

# TAG stl-drools/kie-server:latest