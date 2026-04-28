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
        success {
            slackSend(channel: '#notificaciones-dev', message: '✅ Build exitoso.')
        }
        failure {
            slackSend(channel: '#notificaciones-dev', message: '❌ Build fallido.')
        }
    }
}
