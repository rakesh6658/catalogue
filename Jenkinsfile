pipeline {
    agent { label 'agent-1' }

    stages {
        stage('install dependencies') {
            steps {
                sh 'npm install'
                sh 'npm fund'
                sh 'npm audit fix'
            }
        }

        stage('unit testing') {
            steps {
                echo 'unit testing'
            }
        }
    }
}
