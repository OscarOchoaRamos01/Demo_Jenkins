pipeline {
    agent any

    stages {
        stage('Initialize') {
            steps {
                slackSend(color: '#FFFF00', message: "🚀 Iniciando Pipeline: ${env.JOB_NAME} (Build #${env.BUILD_NUMBER})")
            }
        }

        stage('Build') {
            steps {
                echo 'Compilando el proyecto...'
                sh 'echo "Ejecutando compilación..."'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas unitarias...'
                sh 'true'
            }
        }
    }

    post {
        always {
            slackSend(
                color: '#439FE0',
                message: "📌 PIPELINE TERMINADO: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }

        success {
            slackSend(
                color: '#36a64f',
                message: "✅ ÉXITO: ${env.JOB_NAME} #${env.BUILD_NUMBER} - COMPLETADO"
            )
        }

        failure {
            slackSend(
                color: '#ff0000',
                message: "❌ ERROR: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }
    }
}
