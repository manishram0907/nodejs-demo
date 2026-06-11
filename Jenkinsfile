pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/manishram0907/nodejs-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodejs-demo .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                docker stop nodejs-demo || true
                docker rm nodejs-demo || true
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker run -d \
                --name nodejs-demo \
                -p 8081:3000 \
                nodejs-demo
                '''
            }
        }
    }
}
