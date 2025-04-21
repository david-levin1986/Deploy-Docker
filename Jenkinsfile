pipeline {
    agent any

        environment {
                SSH_KEY = '/var/jenkins_home/.ssh/id_rsa'
                REMOTE_USER = 'jenkinsusr'
                REMOTE_HOST = '192.168.50.120'
                IMAGE_URL = 'docker.io/davidlevin1986/lab:'
                IMAGE_NAME = 'webmotivision1.1.1'
                NEW_TAG = 'webmotivision:1.1.1'
                CONTAINER_NAME = 'web01'
                CONATMER_PORTS = '81:80'



                
            }

    stages {
        stage('Preper Image') {
            steps {
                sh '''
                    ssh -i $SSH_KEY -o StrictHostKeyChecking=no $REMOTE_USER@$REMOTE_HOST "
                        echo "$IMAGE_URL$IMAGE_NAME"
                        sudo docker pull $IMAGE_URL$IMAGE_NAME 
                        echo "Raname Image"
                        sudo docker tag $IMAGE_URL$IMAGE_NAME $NEW_TAG
                        sudo docker image rm $IMAGE_URL$IMAGE_NAME                     
                    "
                '''
            }
        }
                stage('Deploy Motivisin Container') {
            steps {
                sh '''
                    ssh -i $SSH_KEY -o StrictHostKeyChecking=no $REMOTE_USER@$REMOTE_HOST "
                        echo "Deploy Container $NEW_TAG"
                        sudo docker container run --name $CONTAINER_NAME --network ens1 -d -p $CONATMER_PORTS $NEW_TAG
                                            
                    "
                '''
            }
        }

    }
}
