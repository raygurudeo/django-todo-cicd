pipeline {
    agent any
    stages {
        stage("Code") {
            steps {
                git url: "https://github.com/raygurudeo/django-todo-cicd.git", branch: "develop"
            }
        }
        stage("Build And Test") {
            steps {
                docker build . -t web
                echo "Code Built and tested"
            }
        }
        stage("Deploy") {
            steps {
                docker-compose up -d
                echo "Application deployed"
            }
        }
    }
}