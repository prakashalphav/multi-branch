pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
     stage('Deliver for development') {
            when {
                branch 'master' 
            }
            steps {
                sh 'touch /home/ubuntu/prakash/master.txt'
            }
        }
        stage('Deploy for stage') {
            when {
                branch 'stage'  
            }
            steps {
                sh ' touch /home/ubuntu/prakash/stage.txt'
            }
        }
    }
}
