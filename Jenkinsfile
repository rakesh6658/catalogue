pipeline {
    agent { label 'agent-1' }
    environment{
     PACKAGE_VERSION = ''
    }

    stages {

        stage('get version') {
            steps {
                script {
                                        env.PACKAGE_VERSION = env.PACKAGE_VERSION = sh(script: "jq -r .version package.json", returnStdout: true).trim()
                }
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

        stage('scanning') {
            steps {
                 echo 'scanning'
            }
        }

        stage('build') {
            steps {
                sh 'zip -r catalogue.zip . -x "*.zip" ".git/*" '
            }
        }

        stage('publish') {
            steps {
                echo 'published to artifactory'
            }
        }
        stage ('Starting downstream job') {
    steps {
        build job: 'catalogue-deploy', parameters: [
            string(name: 'version', value: "${env.PACKAGE_VERSION}"),
            string(name: 'environment', value: 'dev')
        ], propagate: false
    }
}


    }
}
