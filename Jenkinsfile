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
                echo "Code Built and tested"
            }
        }
        stage("Deploy") {
            steps {
                echo "Application deployed"
            }
        }
    }
}