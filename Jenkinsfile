@Library('Shared') _

pipeline {
    agent any

    stages {

        stage('hello') {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('Code') {
            steps {
                script {
                    clone("https://github.com/rizwangourysk/django-notes-app.git", "main")
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    docker_build("notes-app", "latest", "rizwangourysk")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker_push("notes-app", "latest", "rizwangourysk")
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "This is deploy"
                sh 'docker-compose up -d'
            }
        }
    }
}
