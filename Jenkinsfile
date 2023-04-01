pipeline {
    agent any
    stages {
        stage('Pull latest automation docker image from docker hub') {
            steps {
                sh 'docker pull rugvedk/selenium-docker'
            }
        }
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
    }
    post {
        always {
            archiveArtifacts artifacts: 'output/**'
            sh 'docker-compose down'
        }
    }
}