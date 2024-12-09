pipeline {
    // agent{
    //     label "master-slave"
    // } 
    agent any
    tools {
      maven 'Maven'
    }

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
             input {
                message "Are you sure you want to go ahead"
                ok "Yes I am "
            }
            steps {
                echo 'Deploy on Prod'
            }
        }
    }
    // post {
    //     always{
    //         cleanWs()
    //     }
    // }
}
