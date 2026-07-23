pipeline {
    agent any
    
    stages {
        stage('拉取代码') {
            steps {
                git branch: 'master', url: 'https://github.com/chuxiaoxue/gitProjectPractice.git'
            }
        }
        
        stage('部署到 WSL') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: '65a4f714-3065-44c7-b135-08cc5106a2f1', keyFileVariable: 'SSH_KEY')]) {
                    bat '''
                        ssh -i "%SSH_KEY%" -o StrictHostKeyChecking=no chuxiaoxue@192.168.144.63 ^
                        "cd /mnt/d/python/gitProjectPractice && git pull origin master && ^
                        pkill -f 'python3 -m http.server' 2>/dev/null || true && ^
                        nohup python3 -m http.server 8000 > /dev/null 2>&1 &"
                    '''
                }
            }
        }
    }
}