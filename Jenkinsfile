pipeline {
    agent { label 'agent-1' }

    environment {
    packageVersion = ''
    }

    stages {

        stage('get version') {
            steps {
                script {
                    def packageJson = readJSON(file: 'package.json')
                    packageVersion = packageJson.version
                    echo "version: ${packageVersion}"
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
                echo 'bulding'
            }
        }

        stage('publish') {
            steps {
                echo "Publishing version: $packageVersion"
            }
        }

        stage('Starting downstream job') {
            steps {
                build job: 'catalogue-deploy', parameters: [
                    string(name: 'version', value: "$packageVersion"),
                    string(name: 'environment', value: 'dev')
                ], propagate: false
            }
        }
    }
}
