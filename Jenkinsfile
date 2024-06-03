pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
     stage('Deploy for master') {
            when {
                branch 'master' 
            }

            steps {
                git branch: 'master', url: 'https://github.com/prakashalphav/multi-branch.git'
                sh 'cp ./master.html /var/www/html/master/master.html'
            }
        }
        stage('Deploy for stage') {
            when {
                branch 'stage'  
            }
            
            steps {
                git branch: 'stage', url: 'https://github.com/prakashalphav/multi-branch.git'
                sh 'cp ./stage.html /var/www/html/stage/stage.html'
            }
        }
    }
}
