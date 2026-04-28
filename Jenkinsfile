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
        slackSend(channel: '#canala-nuevo', message: '✅ Build exitoso.')
    }
    failure {
        slackSend(channel: '#canala-nuevo', message: '❌ Build fallido.')
    }
}
}
