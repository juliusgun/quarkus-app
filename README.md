# Quarkus Tutorial with Panache ORM on Openshift

## Generate Project Skeleton

Clone sample source code from

```bash
git clone https://github.com/juliusgun/quarkus-app.git 
 ``` 
 
Or, generate from project skeleton

```bash
mvn io.quarkus.platform:quarkus-maven-plugin:2.2.3.Final:create \
 -DprojectGroupId=com.julius.app.quarkus \
 -DprojectArtifactId=quarkus-app \
 -DclassName="com.julius.app.quarkus.HelloWorld" \
 -Dpath="/hello" \
 -Dextensions="openshift"
 ```
    
## Run in DEV mode

```bash
mvn compile quarkus:dev:
```
run on different port
```bash
mvn compile quarkus:dev: -Dquarkus.http.port=8081
```

## Test Locally (with Java Runtime)
```bash
$ curl localhost:8080/api
```

```bash
hello
```

## Try Hot Reload
Change java class, then Quarkus will hot deploy it.

## Configure the following properties in your application.properties file:

Set the Docker build strategy:
```bash
quarkus.openshift.build-strategy=docker
```

(Optional) If you are using an untrusted certificate, configure the KubernetesClient:
```bash
quarkus.kubernetes-client.trust-certs=true
```

(Optional) Expose the service to create an OpenShift route:
```bash
quarkus.openshift.expose=true
```

## Deploy to OpenShift using Extensions

```bash
./mvnw clean package -Dquarkus.kubernetes.deploy=true -DskipTests
```
