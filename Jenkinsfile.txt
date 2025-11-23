pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/NitishDoddamani/project3-devops-demo.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("project3-demo-image")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    docker.run("project3-demo-image")
                }
            }
        }
    }
}
