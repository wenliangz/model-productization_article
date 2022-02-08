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
                    docker-compose -f docker-compose-etl.yml up
                '''
            }
        }
        stage('Train') {
            steps {
                sh '''
                    docker-compose -f docker-compose-train.yml up
                '''
            }
        }
        stage('predict') {
            steps {
                sh '''
                    docker-compose -f docker-compose-predict.yml up
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