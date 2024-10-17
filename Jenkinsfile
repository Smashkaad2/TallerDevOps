pipeline {
    agent any 
    stages {
        stage('Declarative: Checkout SCM') {
            steps {
                checkout scm
            }
        }
        stage('Install dependencies') {
            steps {
                sh '''
                    apt-get update
                    apt-get install -y python3-venv python3-pylint
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install pylint
                '''
            }
        }
        stage('Run Pylint') {
            steps {
                sh '''
                    . venv/bin/activate
                    pylint your_python_files.py  # Cambia esto por tu archivo o directorio
                '''
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t your_image_name .'
            }
        }
        stage('Deploy Application') {
            steps {
                sh 'docker run -d your_image_name'
            }
        }
    }
}
