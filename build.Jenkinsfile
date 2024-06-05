pipeline {
    agent any
    stages {
        stage('Build docker image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    bat '''
                        copy polybot/app.py .
                        docker login -user $USER --password-stdin $PASS
                        docker build -t ofriz/jenkins-ex:poly-bot-${env.BUILD_NUMBER} .
                        docker push ofriz/jenkins-ex:poly-bot-${env.BUILD_NUMBER}
                    '''
                }
            }
        }
    }
}