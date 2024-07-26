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
        stage('publish artifactory'){
        steps{
             nexusArtifactUploader(
        nexusVersion: 'nexus3',
        protocol: 'http',
        nexusUrl: '://54.198.255.135:8081',
        groupId: 'com.roboshop',
        version: 1.0,
        repository: 'catalogue',
        credentialsId: 'nexus-auth',
        artifacts: [
            [artifactId: catalogue,
             classifier: '',
             file: 'catalogue.zip',
             type: 'zip']
        ]
     )
        }
    }
    
}