pipeline {
    agent any

    stages {
        stage('install dependencies') {
  steps {
    sh 'npm install'
    sh 'npm fund || true'
    sh 'npm audit fix || true'
  }
}
stage('unit testing') {
            steps {
                echo 'unit testing'
            }
        }
        // ('scanning'){
        //     steps{
        //         sh'sonar-scanner'
        //     }
        // }
        stage('build'){
            steps{
                sh 'zip -r catalogue.zip . -x "*.zip" ".git/*" '
            }
        }
        


    }
}
