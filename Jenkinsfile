pipeline {
    agent any

    tools {
        python 'Python3'  // Make sure it's defined in Jenkins tools
    }

    environment {
        SONARQUBE = 'MySonar'  // Must match the name you gave in Jenkins
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/Ress-0722/flask-devops-pipeline.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE}") {
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
