pipeline {
    agent any

    parameters {
        booleanParam(name: 'DEPLOY', description: 'Want to deploy to Production')
    }
    
    environment {
        CURRENT_ENV = 'prodaa'
    }

    stages {
        stage('CEHCKOUT_REPOA') {
            steps {
                checkout ([ $class: 'GitSCM',
                            branches: [[name: '*/main']], 
                            extensions: [], 
                            userRemoteConfigs: [[
                                credentialsId: 'jaintpharsha', 
                                url: 'https://github.com/jaintpharsha/mern_3tire.git'
                            ]]
                        ])
            }
        }

        stage('STAGE1 When branch main') {
            when {
                branch 'main'
            }
            steps {
                echo "This is stage1 running"
                sh ''' 
                    pwd
                    ls -lrt
                    sleep 5
                '''
            }
        }

        stage('when environment') {
            when {
                environment name: 'CURRENT_ENV', value: 'prod'
            }
            steps {
                echo "This is FINAL running"
                sh '''
                    pwd
                    ls -lrt
                    sleep 5
                '''
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