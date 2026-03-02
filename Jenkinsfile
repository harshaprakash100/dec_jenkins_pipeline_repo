pipeline {
    agent any

    parameters {
        booleanParam(name: 'DEPLOY', description: 'Want to deploy to Production')
    }
    
    environment {
        CURRENT_ENV = 'prod'
    }

    stages {
        stage('STAGE1 When branch main') {
            when {
                branch 'main'
            }
            steps {
                echo "This is stage1 running"
                sh ''' 
                    sleep 5
                    exit 1
                '''
            }
        }
        
        stage('when environment') {
            when {
                environment name: 'CURRENT_ENV', value: 'prod'
            }
            steps {
                echo "This is FINAL running"
                sh 'sleep 5'
            }
        }

        stage('when parameter') {
            when {
                expression { params.DEPLOY == true }
            }
            steps {
                echo "This is FINAL running"
                sh 'sleep 5'
            }
        }
    }
}