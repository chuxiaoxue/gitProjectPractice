pipeline {
    agent any
    
    stages {
        stage('部署到 WSL') {
            steps {
                bat '''
                    ssh chuxiaoxue@192.168.144.63 ^
                    "cd /mnt/d/python/gitProjectPractice && git pull && pkill -f 'python3 -m http.server' 2>/dev/null || true && nohup python3 -m http.server 8000 &"
                '''
            }
        }
    }
}