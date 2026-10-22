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
                        sonar-scanner \
                          -Dsonar.projectKey=sonar_task1 \
                          -Dsonar.projectName="SonarQube Lab" \
                          -Dsonar.sources=. \
                          -Dsonar.host.url=http://localhost:9000
                    '''
                }
            }
        }
    }
}
```
