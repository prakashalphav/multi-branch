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
                script {
                    git branch: 'master', url: 'https://github.com/prakashalphav/multi-branch.git'
                    sh 'sudo cp ./master.conf /etc/nginx/sites-available/'
                    sh 'sudo rm -f /etc/nginx/sites-enabled/master.conf'
                    sh 'sudo ln -s /etc/nginx/sites-available/master.conf /etc/nginx/sites-enabled/'
                    sh 'sudo mkdir -p /var/www/html/master'
                    sh 'sudo cp ./master.html /var/www/html/master/master.html'
                    sh 'sudo chown -R www-data:www-data /var/www/html/master'
                    sh 'sudo systemctl start nginx'
                    sh 'sudo systemctl reload nginx'
                }
            }
        }
    }
}
