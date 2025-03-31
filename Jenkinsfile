pipeline {
    agent any
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'dev', description: 'Branch to checkout and build')
    }
    triggers {
        githubPush()
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: "${params.BRANCH_NAME}", url: 'https://github.com/khs-bitcoding/Python-CI-Pipeline-Jenkins.git'
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
                sh '. venv/bin/activate && python3 main.py'
            }
        }

        stage('Run Tests') {
            steps {
                sh '. venv/bin/activate && pytest tests --junitxml=report.xml'
            }
        }
    }
}
