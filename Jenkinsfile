pipeline {
    agent { label 'agent-1' }

    stages {
        stage('install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('unit testing') {
            steps {
                sh 'echo "unit testing"'
            }
        }
    }
}
