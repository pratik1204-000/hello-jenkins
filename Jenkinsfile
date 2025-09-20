pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'jdk11'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/pratik1204-000/hello-jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
