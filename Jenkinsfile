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
        // stage('sonar-scanner') {
        //     steps {
        //         sh 'sonar-scanner'
        //     }
        // }
        stage('build'){
            steps{
                sh'ls -ltr'
                sh 'zip -r  catalogue.zip ./* --exclude=.git --exclude=.zip'
            }
        }
    }
    post{
        always{
            echo "cleaning up workspace"
        deleteDirectories()
        }
        
    }
}