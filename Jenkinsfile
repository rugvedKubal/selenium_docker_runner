pipeline {
    agent any
    stages {
        stage('Pull latest automation docker image from docker hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        image = docker.image('rugvedk/selenium-docker:latest')
                        image.pull()
                    }
                }
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