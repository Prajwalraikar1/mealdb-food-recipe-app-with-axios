pipeline {
    agent any

    environment {
        IMAGE_NAME = "mealdb-app"
        CONTAINER_NAME = "mealdb-container"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Prajwalraikar1/mealdb-food-recipe-app-with-axios.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t ${IMAGE_NAME} .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker run -d --name ${CONTAINER_NAME} -p 3000:3000 ${IMAGE_NAME}'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'docker ps | grep ${CONTAINER_NAME}'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    sh 'docker rm -f ${CONTAINER_NAME}'
                }
            }
        }
    }
}
