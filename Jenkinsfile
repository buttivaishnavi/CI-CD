pipeline {
    agent none

    stages {
        stage('Controller Stage') {
            agent { label 'built-in' }
            steps {
                echo "Running on CONTROLLER"
            }
        }
        stage('Windows Agent Stage') {
            agent { label 'win' }
            steps {
                bat '''echo Running on AGENT'''
            }
        }
        stage('Parallel Test') {
            parallel {
                stage('Controller Lane') {
                    agent { label 'built-in' }
                    steps {
                        echo "Hello from CONTROLLER in parallel"
                    }
                }
                stage('Agent Lane') {
                    agent { label 'win' }
                    steps {
                        bat "echo Hello from AGENT in parallel"
                    }
                }
            }
        }
    }
}
