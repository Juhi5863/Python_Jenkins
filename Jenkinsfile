pipeline {
    agent any
    environment {
        VENV_DIR = 'venv'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Juhi5863/Python_Jenkins.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv $VENV_DIR
                    source $VENV_DIR/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Run Tests') {
            steps {
                sh '''
                    source $VENV_DIR/bin/activate
                    pytest tests/
                '''
            }
        }
        stage('Build Artifact') {
            steps {
                sh '''
                    source $VENV_DIR/bin/activate
                    python setup.py sdist
                '''
            }
        }
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'dist/*.tar.gz', fingerprint: true
            }
        }
    }
}
