pipeline {
    agent any

    stages {
        stage('Pull SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/ariagaluh02/springboot-app.git'
            }
        }
        
        stage('Containerized Apps') {
            steps {
                sh'''
                docker build -t ariagaluh02/springboot-app .
                '''
            }
        }

        stage('Push to Registry') {
            steps {
                sh'''
                docker push ariagaluh02/springboot-app
                '''
            }
        }

        stage('Deploy Apps') {
            steps {
                sh'''
                kubectl apply -f manifest/
                '''
            }
        }   
    }
}