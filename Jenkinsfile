pipeline {
    agent any

        environment {
                SSH_KEY = '/var/jenkins_home/.ssh/id_rsa'
                REMOTE_USER = 'jenkinsusr'
                REMOTE_HOST = '192.168.50.120'
                DOCKER_IMAGE = 'docker.io/davidlevin1986/lab:webmotivision1.1.1'

                
            }

    stages {
        stage('Test Pulling Image') {
            steps {
                sh '''
                    ssh -i $SSH_KEY -o StrictHostKeyChecking=no $REMOTE_USER@$REMOTE_HOST '
                        echo "Pulling Image Motivision Web"
                        docker.io/davidlevin1986/lab:webmotivision1.1.1 
                    '
                '''
            }
        }
    }
}
