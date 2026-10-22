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
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        /opt/sonar-scanner-8.0.1.6346-linux-x64/bin/sonar-scanner \
                          -Dsonar.projectKey=sonar_task1 \
                          -Dsonar.projectName="SonarQube Lab" \
                          -Dsonar.sources=.
                    '''
                }
            }
        }
    }
}
```
