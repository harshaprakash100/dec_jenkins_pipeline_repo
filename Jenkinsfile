pipeline {
    agent any

    environment {
       DOCKER_USER = 'jaintpharsha'
       AWS_ACCESS_KEY = '65197561895639156'
    }

    stages {
        stage('STAGE1') {
            steps {
               echo "DOCKER_USER: ${DOCKER_USER}"
               echo "AWS_ACCESS_KEY: ${AWS_ACCESS_KEY}"

               sh '''
                   env
               '''
            }
        }
        
    }
}