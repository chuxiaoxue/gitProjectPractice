pipeline {
    agent any
    
    stages {
        stage('部署到 WSL') {
            steps {
                bat 'echo "123456" | ssh chuxiaoxue@192.168.144.63 "cd /home/chuxiaoxue/workspace/gitProjectPractice && git pull origin master && echo \\"123456\\" | sudo -S systemctl restart login-app"'
            }
        }
    }
}