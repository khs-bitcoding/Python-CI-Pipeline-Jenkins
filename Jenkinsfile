pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/khs-bitcoding/Python-CI-Pipeline-Jenkins.git'
            }
        }

        stage('Setup Python') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Script') {
            steps {
                sh 'python test.py'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest tests/'
            }
        }
    }
}
