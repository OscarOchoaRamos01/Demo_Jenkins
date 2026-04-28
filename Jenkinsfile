pipeline {
    agent any

    environment {
        SLACK_WEBHOOK_URL = 'PONER_AQUI'
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
                echo "Ejecutando script..."
                bat 'script.bat'
            }
        }

        stage('Test') {
            steps {
                echo "Simulando pruebas..."
                bat 'echo Todo OK'
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