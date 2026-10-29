# DevOps Java App

A tiny Java HTTP application for a Git + Maven + Docker practical.

## Run with Maven
Requires JDK 17+ and Maven:
```bash
mvn package
java -jar target/devops-java-app.jar
```
Open http://localhost:8080 or run `curl http://127.0.0.1:8080`.

## Build and run with Docker
```bash
docker build -t devops-java-app:v1 .
docker run -d --name devops-java-app-test -p 8081:8080 devops-java-app:v1
docker ps
curl http://127.0.0.1:8081
```
The app listens on port 8080 inside the container. Port 8081 on the host is mapped to it.
