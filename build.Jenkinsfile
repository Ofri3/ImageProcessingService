pipeline {
    agent any
    environment {
        IMG_NAME = "polybot:${BUILD_NUMBER}"
    }
    stages {
        stage('Build docker image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    bat """
                        cd polybot
                        docker login -u ${USER} -p ${PASS}
                        docker build -t ${IMG_NAME} .
                        docker tag ${IMG_NAME} ofriz/${IMG_NAME}
                        docker push ofriz/${IMG_NAME}
                    """
                }
            }
        }
    }
}