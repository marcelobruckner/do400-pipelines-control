pipeline {
    agent {
        node {
            label 'nodejs'
        }
    }
    parameters{
        booleanParam(name: "RUN_FRONTEND_TESTS", defaultValue: true)
    }
    stages {
        stage('Run Tests'){
            parallel {
                stage('Backend Tests') {
                    steps {
                        sh 'node ./simple-webapp/backend/test.js'
                    }    
                }
                stage('Frontend Tests') {
                when { expression { params.RUN_FRONTEND_TESTS } }
                    steps {
                        sh 'node ./simple-webapp/frontend/test.js'
                    }
                }
            }
        }

        stage('Deploy'){
            when {
                expression { env.GIT_BRANCH == 'origin/main'}
                beforeInput true
            }
            input {
                message 'Deploy the application?'
            }
            steps {
                echo 'Deploying...'
            }
        }
    }
}