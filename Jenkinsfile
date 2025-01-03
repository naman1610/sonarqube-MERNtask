pipeline {
    agent any

    tools {
        nodejs 'nodejenkins'
    }

    environment {
        SONARQUBE_SERVER = 'sonarqube'
        SONAR_SCANNER = 'C:\\Program Files\\sonar-scanner-6.2.1.4610-windows-x64\\bin'
    }
    
    stages {
        stage ('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage ('Install') {
            steps {
                echo 'Installing dependencies...'
                bat '''
                    npm install
                '''
            }
        }

        stage ('Analysis') {
            environment {
                SONAR_TOKEN = credentials('assignment2-backend')
            }
            steps {
                echo 'Running SonarQube analysis...'
                bat '''
                sonar-scanner -Dsonar.projectKey=naman-assignment2-backend ^
                -Dsonar.sources=. ^
                -Dsonar.host.url=http://localhost:9000 ^
                -Dsonar.token=%SONAR_TOKEN%
                '''
            }
        }
    }
        
    post {
        success {
            echo 'Build success'
        }
        failure {
            echo 'Build failed'
        }
        always {
            echo 'Exiting...'
        }
    }
}