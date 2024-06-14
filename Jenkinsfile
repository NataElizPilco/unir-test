pipeline {
    agent any
    stages {
        stage('Source') {
            steps {
                git 'https://github.com/NataElizPilco/unir-test.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building stage!'
                sh 'make build'
            }
        }
        stage('Run App') {
            steps {
                echo 'Corriendo la aplicacion!'
                sh 'make run'
            }
        }
        stage('Unit tests') {
            steps {
                sh 'make test-unit'
                archiveArtifacts artifacts: 'results/*.xml'
            }
        }
        stage('API tests') {
            steps {
                sh 'make test-api'
                archiveArtifacts artifacts: 'results/*.xml'
            }
        }
        stage('E2E tests') {
            steps {
                echo 'Realizando pruebas E2E'
                //sh 'make test-e2e'
                //archiveArtifacts artifacts: 'results/*.xml'
            }
        }
    }
    post {
        always {
            junit 'results/*_result.xml'
            cleanWs()
        }
    }
}
