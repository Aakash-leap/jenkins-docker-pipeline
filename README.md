jenkins-docker-pipeline/
│
├── Dockerfile
├── docker-compose.yml
├── Jenkinsfile
├── README.md
└── screenshots/
    ├── pipeline-success.png
    └── console-output.png



# Jenkins Docker Pipeline Setup

This project demonstrates how to run Jenkins inside a Docker container and execute Docker-based Jenkins pipelines using Docker Socket Mounting (Docker-outside-of-Docker).

## Technologies Used

- Jenkins
- Docker
- Docker Compose
- Jenkins Pipeline
- Docker Pipeline Plugin
- Node.js

## Architecture

Windows Host
│
├── Docker Desktop
│
└── Jenkins Container
    │
    └── Docker Socket (/var/run/docker.sock)
            │
            └── Node.js Build Container

## Setup

### Build Jenkins Image

```bash
docker compose build
```

### Start Jenkins

```bash
docker compose up -d
```

### Access Jenkins

http://localhost:8080

### Install Plugins

- Docker Pipeline Plugin

## Sample Pipeline

```groovy
pipeline {
    agent {
        docker {
            image 'node:16-alpine'
        }
    }

    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
    }
}
```

## Output

```text
v16.20.2
Finished: SUCCESS
```

## Learning Outcomes

- Jenkins in Docker
- Docker Compose
- Docker Pipeline Plugin
- Docker Socket Mounting (DooD)
- CI/CD Pipeline Basics