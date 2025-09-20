pipeline {
    agent any

    tools {
        maven 'Maven3'   // must match Manage Jenkins -> Global Tool Configuration name
        jdk 'jdk11'      // must match JDK name in Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                // use named parameters (required)
                git url: 'https://github.com/pratik1204-000/hello-jenkins.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // on Windows agents use `bat`
                bat 'mvn -B clean install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn -B test'
            }
            post {
                always {
                    // junit plugin will find surefire xml reports
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
