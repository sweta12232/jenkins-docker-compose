pipeline {
    agent any
    stages {
        stage("verifying tooling") {
            steps {
                sh '''
                    docker --version
                    docker --info
                    docker-compose version
                    curl --version
                '''
            }
        }
        stage("Prune Docker Data") {
            steps {
                sh 'docker system prune -a --volumes -f'
            }
        }
        stage("Start Container") {
            steps {
                sh 'docker compose up -d --no-color --wait'
                sh 'docker compose ps'
            }
        }
    }
}
