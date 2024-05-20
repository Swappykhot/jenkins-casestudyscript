pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    docker.image('ubuntu:latest').inside('-p 82:80') {
                        sh 'apt-get update && apt-get install -y apache2'
                        sh 'cp -r * /var/www/html'
                    }
                }
            }
        }
    }
    post {
        success {
            script {
                if (env.BRANCH_NAME == 'master') {
                    docker.image('ubuntu:latest').inside('-p 82:80') {
                        sh 'apache2ctl -D FOREGROUND'
                    }
                }
            }
        }
    }
}
