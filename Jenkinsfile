pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                // Since Jenkins already checked out the code, we can just verify or use checkout scm, 
                // or point the git plugin to your correct repository and branch:
                git branch: 'main', url: 'https://github.com/Krish-Rajput/jenkins-exp-1.git'
            }
        }

        stage('Python Version') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m pip install --upgrade pip
                    if [ -f requirements.txt ]; then
                        pip3 install -r requirements.txt
                    fi
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    if [ -d tests ]; then
                        python3 -m pytest tests
                    else
                        echo "No tests directory found"
                    fi
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Build completed successfully'
            }
        }
    }

    post {

        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline finished.'
        }
    }
}