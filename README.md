# Jenkins CI/CD Docker Demo

## Project Overview

This project demonstrates a basic CI/CD pipeline using Jenkins and Docker. The pipeline automatically builds a Docker image, tests the Nginx configuration, and deploys the application as a Docker container.

## Technologies Used

* Jenkins
* Docker
* Git
* GitHub
* Nginx
* HTML
* Windows

## Project Structure

```text
jenkins-cicd-demo/
├── app/
│   └── index.html
├── Dockerfile
├── Jenkinsfile
└── README.md
```

## CI/CD Pipeline

The Jenkins pipeline consists of three stages:

### 1. Build

Jenkins builds the Docker image using the Dockerfile.

```text
docker build -t jenkins-cicd-demo .
```

### 2. Test

The pipeline verifies that the Nginx configuration inside the Docker image is valid.

```text
docker run --rm jenkins-cicd-demo nginx -t
```

### 3. Deploy

The pipeline removes the previous container and starts a new container using the newly built image.

```text
docker rm -f jenkins-demo
docker run -d -p 8090:80 --name jenkins-demo jenkins-cicd-demo
```

## Jenkins Configuration

Jenkins is configured to:

1. Clone the project from GitHub.
2. Read the `Jenkinsfile` from the repository.
3. Execute the Build stage.
4. Execute the Test stage.
5. Execute the Deploy stage.

## Application

The application is a simple Nginx web page created using HTML.

The deployed application runs on:

```text
http://localhost:8090
```

## Result

The Jenkins pipeline completed successfully with all three stages:

```text
Build → Test → Deploy
```

The Docker container was successfully created and the web application was deployed using Jenkins.

## Future Improvements

* Add automated GitHub webhook triggers.
* Add application-level health checks.
* Add Docker image versioning.
* Push Docker images to Docker Hub.
* Add automated rollback and monitoring.
* Extend the pipeline with additional testing stages.
