pipeline {
    agent any
    stages {
        stage('Build docker image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    bat '''
                        copy polybot/app.py .
                        docker login -u $USER -p $PASS
                        docker build -t ofriz/jenkins-ex .
                        docker push ofriz/jenkins-ex
                    '''
                }
            }
        }
    }
}