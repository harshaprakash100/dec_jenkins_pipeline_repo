pipeline {
    agent any
    
    triggers {
        cron('H/15 * * * *')
    }

    options {
        ansiColor('xterm')
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
               
                sh '''
                    echo GIT_BRANCH: $GIT_BRANCH
                    echo BRANCH_NAME: $BRANCH_NAME
                '''
            }
        }

        stage('STAGE1 When branch main') {
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main'
                }
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

   
    }
}