pipeline {
    agent any

    environment {
        REMOTE_USER = 'jenkinsusr'
        REMOTE_HOST = '192.168.50.120'
        SSH_CREDENTIALS_ID = 'JenkinsKey' // ה-ID של ה-Credential ב-Jenkins
    }

    stages {
        stage('DeployContainer') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: env.SSH_CREDENTIALS_ID, keyFileVariable: 'SSH_KEY')]) {
                    sh '''
                        ssh -i $SSH_KEY $REMOTE_USER@$REMOTE_HOST << 'EOF'
                            mkdir -p /tmp/jenkinstest
                            echo "Directory created successfully"
                        EOF
                    '''
                }
            }
        }
    }
}