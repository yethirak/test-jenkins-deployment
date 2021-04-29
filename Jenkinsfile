pipeline {
    agent  { label 'jenkins-slave'}
    
    stages {
        stage('Checkout source') {
            steps {
                git branch: 'main', url: 'https://github.com/yethirak/test-jenkins-deployment.git'
            }
        }
    }
} 