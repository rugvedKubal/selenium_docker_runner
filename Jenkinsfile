pipeline {
    agent any
    stages {
        stage('Start selenium grid using docker-compose file in project') {
            steps {
                sh 'docker-compose up -d hub chrome firefox'
            }
        }
        stage('Run automation execution using docker-compose file in project') {
            steps {
                sh 'docker-compose up testInChrome testInFirefox'
            }
        }
        stage('Stop selenium grid') {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}