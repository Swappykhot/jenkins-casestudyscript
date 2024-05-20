pipeline {
    agent {
        docker {
            image 'ubuntu:latest'
            args '-p 82:80'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'apt-get update && apt-get install -y apache2'
                sh 'cp -r * /var/www/html'
            }
        }
    }
    post {
        success {
            script {
                if (env.BRANCH_NAME == 'master') {
                    sh 'docker run -d -p 82:80 ubuntu:latest apache2ctl -D FOREGROUND'
                }
            }
        }
    }
}
