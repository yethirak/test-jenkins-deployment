pipeline {
    agent  { label 'jenkins-slave'}
    environment {
    registry = "localhost:5000"
    repo-name = "test-jenkins-deployment"
    }
    stages {
        stage('Checkout source') {
            steps {
                git branch: 'main', url: 'https://github.com/yethirak/$repo-name.git'
            }
        }
        stage('npm install and build') {
            steps {
                sh 'npm install && npm run build'
            }
        }
        stage('docker build') {
            steps {
                sh 'docker build -t $registry/$repo-name:$BUILD_NUMBER .'
            }
        }
        stage('docker push') {
            steps {
                sh 'docker push $registry/$repo-name:$BUILD_NUMBER'
            }
        }
        stage('clean up docker image') {
            steps {
                sh 'docker rmi $registry/$repo-name:$BUILD_NUMBER'
            }
        }
        stage('kube deploy') {
            steps {
                sh 'cat deployment.yaml | sed "s/{{BUILD_NUMBER}}/:$BUILD_NUMBER:=1/g" | kubectl apply -f - '
            }
        }
    }
} 
