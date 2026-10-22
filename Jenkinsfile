pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube Lab') {
                    sh '''
                        /opt/sonar-scanner/bin/sonar-scanner \
                          -Dsonar.projectKey=jenkins token \
                          -Dsonar.projectName="SonarQube Lab" \
                          -Dsonar.sources=.
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'SonarQube analysis completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the Jenkins console output.'
        }
    }
}
