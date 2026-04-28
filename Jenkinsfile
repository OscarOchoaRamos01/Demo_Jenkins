pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Construyendo...'
                bat 'echo Build OK'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                bat 'echo Test OK'
            }
        }
    }

    post {
        always {
            slackSend(
                channel: '#canala-nuevo',
                message: "🚀 Pipeline ejecutado: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        success {
            slackSend(
                channel: '#canala-nuevo',
                message: "✅ ÉXITO: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        failure {
            slackSend(
                channel: '#canala-nuevo',
                message: "❌ ERROR: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }
    }
}
