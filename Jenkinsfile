pipeline {
    agent {
        docker { image 'python:3.10' }
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Application') {
            steps {
                sh 'python app.py'
            }
        }
    }
}

