pipeline {
    agent any

        environment {
                SSH_KEY = '/var/jenkins_home/.ssh/id_rsa'
                REMOTE_USER = 'jenkinsusr'
                REMOTE_HOST = '192.168.50.120'

                
            }

    stages {
        stage('SSH TEST') {
            steps {
                sh '''
                    ssh -i \$SSH_KEY \$REMOTE_USER@\$REMOTE_HOST <<EOF
                    sudo echo "David" > /tmp/david.tst
                '''
            }
        }
    }
}