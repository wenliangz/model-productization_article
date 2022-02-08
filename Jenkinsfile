pipeline {
    agent any
    stages {
        stage('Verify') {
            steps {
                sh '''
                  python3 --version
                '''
                sh 'printenv'
                sh 'ls -l "$WORKSPACE"'
            }
        }
        stage('Unit Test') {
            steps {
                sh '''
                    python3 -m pytest tests/
                '''
            }
        }
        stage('ETL') {
            steps {
                sh '''
                    python3 etl.py
                '''
            }
        }
        stage('Train') {
            steps {
                sh '''
                    python3 train.py
                '''
            }
        }
        stage('Predict') {
            steps {
                sh '''
                    python3 predict.py
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                    docker-compose -f docker-compose-fastapi.yml up -d
                '''
            }
        }

    }
}