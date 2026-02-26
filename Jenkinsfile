pipeline {
    agent any

    environment {
        SERVER_IP     = '172.31.10.42'
        SSH_CREDENTIAL = 'gym-key'
        REPO_URL      = 'https://github.com/Sudarshan-Mane-2004/Gym-Static-Website.git'
        BRANCH        = 'main'
        REMOTE_USER   = 'ec2-user'
        REMOTE_PATH   = '/var/www/html'
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: "${BRANCH}", url: "${REPO_URL}"
            }
        }

        stage('Deploy to Target Server') {
            steps {
                sshagent(['wrong-credential-id']) {
                    sh """
                        ssh -o StrictHostKeyChecking=no ${REMOTE_USER}@${SERVER_IP} 'mkdir -p ${REMOTE_PATH}'
                        scp -o StrictHostKeyChecking=no -r * ${REMOTE_USER}@${SERVER_IP}:${REMOTE_PATH}
                    """
                }
            }
        }

        stage('Restart Nginx') {
            steps {
                sshagent([SSH_CREDENTIAL]) {
                    sh """
                        ssh -o StrictHostKeyChecking=no ${REMOTE_USER}@${SERVER_IP} '
                            sudo systemctl restart nginx
                        '
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful'
        }
        failure {
            echo 'Deployment Failed'
        }
    }
}