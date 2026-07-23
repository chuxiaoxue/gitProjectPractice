pipeline {
    agent any
    
    stages {
        stage('部署到 WSL') {
            steps {
                bat 'ssh chuxiaoxue@192.168.144.63 "cd /home/chuxiaoxue/workspace/gitProjectPractice && git pull origin master && sudo systemctl restart login-app"'
            }
        }
    }
}