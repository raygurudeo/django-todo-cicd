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
                sh 'docker build . -t django-todo-cicd'
                echo "Code Built and tested"
            }
        }
        stage("Push To Dockerhub") {
            steps {
                withCredentials([usernamePassword(credentialsId:"dockerhub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                    sh "docker tag django-todo-cicd ${env.dockerHubUser}/django-todo-cicd"
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                    sh "docker push ${env.dockerHubUser}/django-todo-cicd:latest"
                    echo "Image pushed to Dockerhub"
                }
            }
        }
    }
}