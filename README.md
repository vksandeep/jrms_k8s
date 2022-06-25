# Drools setup




## Build docker image k8s server
```
cd dkr_kie_server
docker build -t icodecraft/kie-server:latest .
```


## Build docker image k8s wb server
```
cd dkr_kie_wb
docker build -t icodecraft/kie-wb:latest .
```

## Publish Images to remote docker registry where k8s runs
```
docker login
docker push   
```

## First time create namespace drools
```
kubectl create namespace drools
```

## Deploy k8s PV, Kie server, Kie wb, config, secrets
```
cd k8s-manifest
kubectl apply -f .
```

## Endpoints

Kie WB

http://localhost:31001/business-central/kie-wb.jsp

Kie Server
http://localhost:31002/kie-server/services/rest/server/


## Delete k8s PV, Kie server, Kie wb
```
cd k8s-manifest
kubectl delete -f .
```


## Ref

http://www.mastertheboss.com/bpm/drools/getting-started-with-business-central-workbench/

https://stackoverflow.com/questions/54073794/kubernetes-persistent-volume-on-docker-desktop-windows

https://asbnotebook.com/set-up-drools-business-central-and-kie-server-on-wildfly/

Replace /opt/jboss/wildfly/standalone/configuration/standalone-full-drools.xml by customizing :

–server-config=standalone-xml: Used to start the WildFly server on full mode.
org.kie.server.id: A unique KIE server identifier. We are setting this property to wildfly-kieserver.
org.kie.server.user: Username to be set to access KIE server. It’s kieserver in our example. This is the application user we have created earlier.
org.kie.server.pwd: Password to access the KIE server. This is the password of the WildFly application user(kieserver), that we have created earlier.
org.kie.server.location: HTTP location where the KIE server gets exposed.
org.server.controller.user: Username for accessing the KIE REST API.
org.server.controller.pwd: Password for accessing the KIE REST API.
org.kie.server.controller: The KIE REST server location. This URL used by the client applications to invoke the drools rules, that are deployed on the KIE server.

