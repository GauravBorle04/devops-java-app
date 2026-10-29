pipeline {
    agent any

    stages {
        stage('Checkout GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR-USERNAME/devops-java-app.git'
            }
        }

        stage('Build Java') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-java-app:v1 .'
            }
        }

        stage('Ansible Health Check') {
            steps {
                sh 'ansible local -m ping'
                sh 'ansible local -m command -a "hostname"'
            }
        }
    }

    post {
        success {
            echo 'All pipeline stages completed successfully!'
        }
    }
}
