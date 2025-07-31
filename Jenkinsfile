pipeline {
    agent { label 'agent-1' }

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
        


    }
}
