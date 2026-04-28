pipeline {
    agent any

    environment {
        LANG = "en_US.UTF-8"
    }

    stages {

        stage('Initialize') {
            steps {
                slackSend(
                    message: "INICIO del pipeline: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
                )
            }
        }

        stage('Build') {
            steps {
                echo 'Construyendo proyecto...'
                bat 'echo Build OK'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                bat 'echo Tests OK'
            }
        }
    }

    post {

        success {
            slackSend(
                message: "EXITO: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        failure {
            slackSend(
                message: "ERROR: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        always {
            slackSend(
                message: "PIPELINE TERMINADO: ${env.JOB_NAME}"
            )
        }
    }
}
