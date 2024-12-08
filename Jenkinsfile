pipeline {
    // agent{
    //     label "master-slave"
    // } 
    agent any
    stages {
        stage('Test') {
            steps {
                git 'https://github.com/mohit12390/myproj.git'
                sh 'mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn install'
            }
        }
        stage('Deploy on Tomcat (Test)') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://localhost:8085')], contextPath: '/app', war: '**/*.war'
            }
        }
        stage('Deploy on prod') {
            steps {
                echo 'Deploy on Prod'
            }
        }
    }
}
