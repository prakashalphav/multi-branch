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
            sh 'sudo rm -rf /etc/nginx/sites-available/default'
        }
     }
     stage('Deploy for master') {
            when {
                branch 'master' 
            }

            steps {
                git branch: 'master', url: 'https://github.com/prakashalphav/multi-branch.git'
                sh 'cp ./master.conf /etc/nginx/sites-available/'
                sh 'sudo ln -s /nginx-sites-available/master.conf /etc/nginx-sites-enabled/
                sh 'mkdir /var/www/html/master
                sh 'cp ./master.html /var/www/html/master/master.html'
                sh 'sudo systemctl reload nginx'
            }
        }
}
