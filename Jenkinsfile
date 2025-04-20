pipeline {
    agent any

        environment {
                SSH_KEY = '/var/jenkins_home/.ssh/id_rsa'
                REMOTE_USER = 'jenkinsusr'
                REMOTE_HOST = '192.168.50.120'

                
            }

    stages {
        stage('Create file on remote server') {
            steps {
                sh '''
                    ssh -i $SSH_KEY -o StrictHostKeyChecking=no $REMOTE_USER@$REMOTE_HOST '
                        rm -rf /tmp/test
                        echo "Hello From Jenkins" > /tmp/test.txt
                    '
                '''
            }
        }
    }
}
