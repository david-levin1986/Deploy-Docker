pipeline {
    agent any

             environment {
                SSH_KEY = '/var/jenkins_home/.ssh/id_rsa'
                REMOTE_USER = 'jenkinsusr'
                REMOTE_HOST = '192.168.50.125'
                
            }

    stages {
 
        stage('DeployContainer') {
            steps {
                sh '''
                    ssh -i $SSH_KEY $REMOTE_USER@$REMOTE_HOST <<'EOF'
                    mkdir -p /tmp/davidtest
                    echo "Hello David" > /tmp/davidtest/davidtest.txt

                '''
            }
        }
    }
}