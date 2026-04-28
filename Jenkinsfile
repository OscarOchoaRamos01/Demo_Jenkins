pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Construyendo...'
            }
        }
    }

    post {
        always {
            slackSend(
                channel: '#canala-nuevo',
                message: "🚀 PIPELINE EJECUTADO: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
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
