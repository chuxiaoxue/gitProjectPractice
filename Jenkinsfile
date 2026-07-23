pipeline {
    agent any
    
    stages {
        stage('部署到 WSL') {
            steps {
                bat 'ssh chuxiaoxue@192.168.144.63 "cd /home/chuxiaoxue/workspace/gitProjectPractice && git pull origin master && pkill -f \'python3 -m http.server\' 2>/dev/null || true && nohup python3 -m http.server 8000 > /tmp/server.log 2>&1 & disown"'
            }
        }
    }
}