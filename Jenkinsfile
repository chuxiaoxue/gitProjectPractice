pipeline {
    agent any
    
    stages {
        stage('部署到 WSL') {
            steps {
                bat '''
                    echo "=== 开始部署 ==="
                    ssh chuxiaoxue@192.168.144.63 ^
                    "cd /home/chuxiaoxue/workspace/gitProjectPractice && ^
                    echo '当前目录:' && pwd && ^
                    echo '拉取代码...' && git pull origin master && ^
                    echo '停止旧服务...' && pkill -f 'python3 -m http.server' 2>/dev/null || true && ^
                    echo '启动新服务...' && nohup python3 -m http.server 8000 > /tmp/server.log 2>&1 & && ^
                    sleep 2 && ^
                    echo '检查服务状态:' && ps aux | grep python3 && ^
                    echo '=== 部署完成 ==='"
                '''
            }
        }
    }
}