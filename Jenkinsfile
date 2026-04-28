pipeline {
    agent any

    environment {
        SLACK_WEBHOOK_URL = credentials('slack-webhook')
    }

    stages {
        stage('Inicio') {
            steps {
                script {
                    enviarSlack("🚀 Pipeline iniciado: ${env.JOB_NAME}")
                }
            }
        }

        stage('Build') {
            steps {
                bat 'script.bat'
            }
        }

        stage('Test') {
            steps {
                bat 'echo OK'
            }
        }
    }

    post {
        success {
            script {
                enviarSlack("✅ ÉXITO: ${env.JOB_NAME} #${env.BUILD_NUMBER}")
            }
        }
        failure {
            script {
                enviarSlack("❌ ERROR: ${env.JOB_NAME} #${env.BUILD_NUMBER}")
            }
        }
    }
}

def enviarSlack(String mensaje) {
    bat """
    curl -X POST -H "Content-type: application/json" ^
    --data "{\\"text\\":\\"${mensaje}\\"}" ^
    %SLACK_WEBHOOK_URL%
    """
}
