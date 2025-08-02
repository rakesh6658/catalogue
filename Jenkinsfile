pipeline {
    agent {label 'agent-1'}

    stages {

        stage('get version'){
            steps{
            script{
                def version = sh(script: "jq -r .version package.json", returnStdout: true).trim()
                    echo "Version from package.json is: ${version}"
            }
        }
        
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
        stage('publish'){
            steps{
                echo 'pulished to artifactory'
            }
        }
        


    }
}
