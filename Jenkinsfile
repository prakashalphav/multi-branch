pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
     stage('Install') {
        steps {
            sh 'sudo apt-get update'
            sh 'sudo apt-get install nginx -y'
            sh 'rm -rf /etc/nginx/sites-available/default'
        }
     }
     stage('Deploy for master') {
            when {
                branch 'master' 
            }

            steps {
                git branch: 'master', url: 'https://github.com/prakashalphav/multi-branch.git'
                sh 'cp ./master.html /var/www/html/master/master.html'
                sh 'sudo systemctl reload nginx'
            }
        }
        stage('Deploy for stage') {
            when {
                branch 'stage'  
            }
            
            steps {
                git branch: 'stage', url: 'https://github.com/prakashalphav/multi-branch.git'
                sh 'cp ./stage.html /var/www/html/stage/stage.html'
                sh 'sudo systemctl reload nginx'
            }
        }
    }
}
