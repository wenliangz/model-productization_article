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
                    pytest
                '''
            }
        }
        stage('ETL') {
            steps {
                sh '''
                    python3 ./scripts/etl.py
                '''
            }
        }
        stage('Train') {
            steps {
                sh '''
                    python3 ./scripts/train.py
                '''
            }
        }
        stage('Predict') {
            steps {
                sh '''
                    python3 ./scripts/predict.py
                '''
            }
        }

    }
}