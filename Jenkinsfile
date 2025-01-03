pipeline {
    agent any

    tools {
        nodejs 'nodejenkins'
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
                sh 'npm install'
            }
        }
    }
}