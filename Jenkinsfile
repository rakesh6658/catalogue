pipeline {
    agent { label 'agent-1' }

    environment {
        PACKAGE_VERSION = ''
    }

    stages {

        stage('get version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    env.PACKAGE_VERSION = packageJson.version
                    echo "Version from package.json: ${env.PACKAGE_VERSION}"
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

        // Optional build stage
        // stage('build') {
        //     steps {
        //         sh 'zip -r catalogue.zip . -x "*.zip" ".git/*" '
        //     }
        // }

        stage('publish') {
            steps {
                echo "Publishing version: ${env.PACKAGE_VERSION}"
            }
        }

        stage('Starting downstream job') {
            steps {
                build job: 'catalogue-deploy', parameters: [
                    string(name: 'version', value: "${env.PACKAGE_VERSION}"),
                    string(name: 'environment', value: 'dev')
                ], propagate: false
            }
        }
    }
}
