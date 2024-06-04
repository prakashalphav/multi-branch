
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
        stage('Deploy for stage') {
            when {
                branch 'stage' 
            }
            steps {
                script {
                    git branch: 'stage', url: 'https://github.com/prakashalphav/multi-branch.git'
                    sh 'sudo cp ./stage.conf /etc/nginx/sites-available/'
                    sh 'sudo rm -f /etc/nginx/sites-enabled/stage.conf'
                    sh 'sudo ln -s /etc/nginx/sites-available/stage.conf /etc/nginx/sites-enabled/'
                    sh 'sudo mkdir -p /var/www/html/stage'
                    sh 'sudo cp ./stage.html /var/www/html/stage/stage.html'
                    sh 'sudo chown -R www-data:www-data /var/www/html/stage'
                    sh 'sudo systemctl start nginx'
                    sh 'sudo systemctl reload nginx'
                }
            }
        }
    }
}
