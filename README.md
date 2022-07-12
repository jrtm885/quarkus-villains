# Curl commands

Criacao:
curl -X POST http://localhost:8084/api/villains -H "Content-type:application/json" -d "{\"name\":\"teste\", \"level\":2}" -v

GET ALL
curl -X GET http://localhost:8084/api/villains

curl -X GET http://172.18.218.108:8084/api/villains
172.18.218.108

# Cluster Kubernetes

host banco de dados:  psql-test-postgresql.default.svc.cluster.local:5432
password: ijsRosxWNm

Build image: 
docker build -t jr-martinez/rest-villains:0.1 .

Run imagem: 
kubectl run villains --image=jr-martinez/rest-villains:0.1 --port 8084

Port-forward: 
kubectl port-forward pods/villains 8084:8084

Recuperar secrets: 
kubectl get secret psql-test-postgresql -o jsonpath="{.data}"

kubectl expose deployment demo --type=LoadBalancer --name=demo-service
kubectl expose deployment villains-deployment --type=LoadBalancer --name=villains-service
kubectl expose deployment villains-deployment --type=LoadBalancer --name=villains-service

docker run -p 8080:8080 -p 50000:50000 -v C:/dev/volumes/jenkins:/var/jenkins_home jenkins/jenkins:lts-jdk11

C:\dev\volumes\jenkins

C:\dev\tools\graalvm-ce-java11-windows-amd64-22.1.0\graalvm-ce-java11-22.1.0
# rest-villains Project

This project uses Quarkus, the Supersonic Subatomic Java Framework.

If you want to learn more about Quarkus, please visit its website: https://quarkus.io/ .

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```shell script
./mvnw compile quarkus:dev
```

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

## Packaging and running the application

The application can be packaged using:
```shell script
./mvnw package
```
It produces the `quarkus-run.jar` file in the `target/quarkus-app/` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/quarkus-app/lib/` directory.

The application is now runnable using `java -jar target/quarkus-app/quarkus-run.jar`.

If you want to build an _über-jar_, execute the following command:
```shell script
./mvnw package -Dquarkus.package.type=uber-jar
```

The application, packaged as an _über-jar_, is now runnable using `java -jar target/*-runner.jar`.

## Creating a native executable

You can create a native executable using: 
```shell script
./mvnw package -Pnative
```

Or, if you don't have GraalVM installed, you can run the native executable build in a container using: 
```shell script
./mvnw package -Pnative -Dquarkus.native.container-build=true
```

You can then execute your native executable with: `./target/rest-villains-1.0.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/maven-tooling.

## Related Guides


## Provided Code

### RESTEasy Reactive

Easily start your Reactive RESTful Web Services

[Related guide section...](https://quarkus.io/guides/getting-started-reactive#reactive-jax-rs-resources)
