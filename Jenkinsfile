pipeline {
    agent  { label 'jenkin-slave'}}
    
    stages {
        stage('Checkout source') {
            steps {
                git branch: 'main', url: 'https://github.com/yethirak/test-jenkins-deployment.git'
            }
        }
    }
} 