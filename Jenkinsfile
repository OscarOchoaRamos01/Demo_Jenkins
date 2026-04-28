pipeline {
    agent any

    environment {
        LANG = "en_US.UTF-8"
    }

    stages {

        stage('Initialize') {
            steps {
                slackSend(
                    color: '#FFFF00',
                    message: "🚀 INICIO del pipeline: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
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
                color: '#36a64f',
                message: "✅ ÉXITO: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        failure {
            slackSend(
                color: '#ff0000',
                message: "❌ ERROR: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        always {
            slackSend(
                color: '#439FE0',
                message: "📌 PIPELINE TERMINADO: ${env.JOB_NAME}"
            )
        }
    }
}
