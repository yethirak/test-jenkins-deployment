pipeline {
    agent  any

    tools {nodejs "node"}

    
    stages {
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/yethirak/test-jenkins-deployment.git'
                sh 'npm install'
            }
        }
    }
} 