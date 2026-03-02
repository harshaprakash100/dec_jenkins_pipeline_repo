pipeline {
    agent any

    stages {
        stage('STAGE1') {
            steps {
               echo "This is stage1 running"
               sh 'sllep 5'
            }
        }
        
        stage('PARALLEL TESTING') {
            parallel {
                stage('WINDOWS TESTING') {
                    steps {
                    echo "This is WINDOWS testing running"
                    sh 'sllep 5'
                    }
                }

                stage('MACOS TESTING') {
                    steps {
                        echo "This is MACOS testing running"
                        sh 'sllep 5'
                    }
                }
            }
        }

        stage('FINAL') {
            steps {
               echo "This is FINAL running"
               sh 'sllep 5'
            }
        }
    }
}