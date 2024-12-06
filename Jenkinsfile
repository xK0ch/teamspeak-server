pipeline {
    agent any

    environment {
        TEAMSPEAK_DB_PASSWORD = credentials('teamspeak-db-password')
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                    withEnv(["TEAMSPEAK_DB_PASSWORD=${TEAMSPEAK_DB_PASSWORD}"]) {
                        sh 'docker compose -f docker-compose-teamspeak-server.yml down'
                        sh 'docker image prune -af'
                        sh 'docker compose -f docker-compose-teamspeak-server.yml up -d'
                    }
                }
            }
        }
    }
}