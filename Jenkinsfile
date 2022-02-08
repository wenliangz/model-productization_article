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
                    python3 -m pytest
                '''
            }
        }
        stage('ETL') {
            steps {
                sh '''
                    cd scripts
                    python3 etl.py
                '''
            }
        }
        stage('Train') {
            steps {
                sh '''
                    cd scripts
                    python3 train.py
                '''
            }
        }
        stage('Predict') {
            steps {
                sh '''
                    cd scripts
                    python3 predict.py
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                    docker-compose -f docker-compose-fastapi.yml up --build
                '''
            }
        }

    }
}