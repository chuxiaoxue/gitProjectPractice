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
                sshagent(['wsl-ssh-credentials-id']) {
                    sh '''
                        ssh chuxiaoxue@192.168.144.63 << 'EOF'
                            cd /mnt/d/python/gitProjectPractice
                            git pull origin master
                            pkill -f "python3 -m http.server" 2>/dev/null || true
                            nohup python3 -m http.server 8000 > /dev/null 2>&1 &
                            echo "部署成功！"
                        EOF
                    '''
                }
            }
        }
    }
}