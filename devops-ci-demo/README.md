
# devops-ci-demo

Spring Boot REST API with a Jenkins CI/CD pipeline and Dockerized deployment.

## Quickstart (Local)
```bash
# 1) Build & test
mvn -B clean package

# 2) Run the app
java -jar target/app.jar
# Open: http://localhost:8080/hello
```

## Docker (Local)
```bash
docker build -t demo-app:latest .
docker rm -f demo-app || true
docker run -d --name demo-app -p 8080:8080 demo-app:latest
# Open: http://localhost:8080/hello
```

## Jenkins Pipeline (Declarative)
- Configure tools in Jenkins (Manage Jenkins → Global Tool Configuration):
  - Maven named: **Maven3**
  - JDK named: **jdk17**
- Create a Pipeline Job with "Pipeline script from SCM" and point to this repo.
- The `Jenkinsfile` covers: checkout → build → unit tests → docker build → run container.

## Push to GitHub (example)
```bash
git init
git add .
git commit -m "Initial commit: Spring Boot + Jenkins + Docker pipeline"
git branch -M main
git remote add origin https://github.com/<your-username>/devops-ci-demo.git
git push -u origin main
```
