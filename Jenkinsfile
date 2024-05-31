pipeline {
    agent any

    environment {
        // Define the Python version and virtual environment path
        PYTHON_VERSION = '3.10'
        VENV_DIR = 'venv'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the version control system
                git 'https://github.com/TestUserSemester3/webpage.git'
            }
        }

        stage('Set Up Python') {
            steps {
                script {
                    // Check if Python is installed
                    sh 'python3 --version || { echo "Python is not installed"; exit 1; }'
                    
                    // Create a virtual environment
                    sh "python3 -m venv ${env.VENV_DIR}"

                    // Activate the virtual environment
                    sh ". ${env.VENV_DIR}/bin/activate"

                    // Upgrade pip
                    sh "pip install --upgrade pip"
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Activate the virtual environment and install Flask
                    sh ". ${env.VENV_DIR}/bin/activate && pip install Flask"
                }
            }
        }

        stage('Run Flask Application') {
            steps {
                script {
                    // Run the Flask application on port 80
                    sh ". ${env.VENV_DIR}/bin/activate && sudo python3 app.py"
                }
            }
        }
    }
}
