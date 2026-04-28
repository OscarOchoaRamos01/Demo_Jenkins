pipeline {
    agent any

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
                bat 'echo Build ejecutado correctamente'
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
                channel: '#canala-nuevo',
                message: "✅ ÉXITO: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        failure {
            slackSend(
                color: '#ff0000',
                channel: '#canala-nuevo',
                message: "❌ ERROR: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        always {
            slackSend(
                color: '#439FE0',
                channel: '#canala-nuevo',
                message: "📌 FIN DEL PIPELINE: ${env.JOB_NAME}"
            )
        }
    }
}
