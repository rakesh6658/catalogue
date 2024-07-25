pipeline {
    agent {
         node { label 'agent1'}
    }
    stages {
        stage('installing dependencies') {
            steps {
                
                sh ' npm install '
            }
        }
        stage(' unit Test') {
            steps {
                echo "unit testing"
            }
        }
        stage('Deploy') {
            steps {
                echo "ready for deployment"
            }
        }
    }
}