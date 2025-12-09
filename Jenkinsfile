pipeline {
    agent any

    tools {
       go "1.24.1"
    }

    stages {
        stage('Test') {
              steps {
                   sh "go test ./..."
              }
        }
        stage('Build') {
            steps {
                sh "go build main.go"
            }
        }
        stage('Build Docker Image') {
            steps {
                sh "docker build . --tag ttl.sh/myapp:1h"
            }
        }
        stage('Docker Run Image') {
            steps {
                sh "ssh laborant@docker 'docker run --detach --publish 4444:4444 ttl.sh/myapp:1h'"
            }
        }
    }
}
