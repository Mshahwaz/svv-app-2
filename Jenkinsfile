pipeline {
    agent any
    environment {
        REPO = "app2-flask"
        TAG = "${BUILD_NUMBER}"
        PORT = "5050"
    }
    stages{
        stage('Build'){
            steps{
                sh 'docker build -t "$REPO:$TAG" . '
            }
        }
        stage('Deploy'){
            steps{
                sh ' docker rm $REPO:$TAG || true '
                sh ' docker run -d -p $PORT:$PORT $REPO:$TAG '
            }
        }
    }
}