pipeline {
    agent any

             environment {
                SSH_KEY = '/var/jenkins_home/.ssh/id_rsa'
                REMOTE_USER = 'jenkinsusr'
                REMOTE_HOST = '192.168.50.120'
                SSH_KEY = 'JenkinsKey'
                
            }

    stages {
 
        stage('DeployContainer') {
            steps {
                sh '''
                    withCredentials([sshUserPrivateKey(credentialsId: env.SSH_KEY, keyFileVariable: 'SSH_KEY')]) {
                    ssh -i $SSH_KEY $REMOTE_USER@$REMOTE_HOST <<'EOF'
                    mkdir -p /tmp/jenkinstest
                    

                '''
            }
        }
    }
}