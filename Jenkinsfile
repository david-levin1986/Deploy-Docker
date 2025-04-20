pipeline {
    agent any

    stages {
        stage('Create file on remote server') {
            steps {
                sh '''
                    ssh -i /var/jenkins_home/.ssh/id_rsa -o StrictHostKeyChecking=no jenkinsusr@192.168.50.120 '
                        mkdir -p /tmp/test &&
                        echo "Hello From Jenkins" > /tmp/test/test.txt
                    '
                '''
            }
        }
    }
}
