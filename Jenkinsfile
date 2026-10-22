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
                        /opt/sonar-scanner-8.0.1.6346-linux/bin/sonar-scanner \
                          -Dsonar.projectKey=sonar_task1 \
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
