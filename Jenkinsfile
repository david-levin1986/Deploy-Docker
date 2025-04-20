pipeline {
    agent any

    environment {
        REMOTE_USER = 'jenkinsusr'
        REMOTE_HOST = '192.168.50.120'
        SSH_CREDENTIALS_ID = '39b74b2a-deb4-4a33-8a75-adebe9574f76'
    }

    stages {
        stage('Create and Verify File') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: env.SSH_CREDENTIALS_ID, keyFileVariable: 'SSH_KEY')]) {
                    sh '''
                        echo "Local file content" > local_test.txt
                        scp -i $SSH_KEY local_test.txt $REMOTE_USER@$REMOTE_HOST:/tmp/jenkins_test.txt
                        ssh -i $SSH_KEY $REMOTE_USER@$REMOTE_HOST << 'EOF'
                            cat /tmp/jenkins_test.txt
                            ls -l /tmp/jenkins_test.txt
                        EOF
                    '''
                }
            }
        }
    }
}