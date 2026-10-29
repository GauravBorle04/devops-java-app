pipeline {
    agent any

    stages {
        stage('Checkout GitHub') {
            steps {
                echo 'Repository checked out by Jenkins SCM'
            }
        }

        stage('Build Java') {
            steps {
                dir('devops-java-app') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('devops-java-app') {
                    sh 'docker build -t devops-java-app:v1 .'
                }
            }
        }

        stage('Ansible Health Check') {
            steps {
                sh 'ansible localhost -m ping -c local'
                sh 'ansible localhost -m command -a "hostname" -c local'
            }
        }
    }

    post {
        success {
            echo 'All pipeline stages completed successfully!'
        }
    }
}
