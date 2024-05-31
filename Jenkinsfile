pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/TestUserSemester3/webpage.git'
            }
        }

        stage('Set Up and Install') {
            steps {
                sh '''
                    python3 --version || { echo "Python is not installed"; exit 1; }
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip Flask
                '''
            }
        }

        stage('Run Flask Application') {
            steps {
                sh '''
                    . venv/bin/activate
                    python3 app.py
                '''
            }
        }
    }
}
