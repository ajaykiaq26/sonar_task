```groovy
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
                        /usr/local/bin/sonar-scanner \
                          -Dsonar.projectKey=sonar_task1 \
                          -Dsonar.projectName="SonarQube Lab" \
                          -Dsonar.sources=.
                    '''
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 5, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
```
