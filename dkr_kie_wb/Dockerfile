# Dockerfile

FROM jboss/drools-workbench-showcase:latest

RUN rm /opt/jboss/wildfly/standalone/configuration/standalone-full-drools.xml
COPY standalone-full-drools.xml /opt/jboss/wildfly/standalone/configuration

# TAG stl-drools/kie-wb:latest