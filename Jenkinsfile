pipeline {
    agent any

    triggers {
        pollSCM('* * * * *') // 매 5분마다 체크
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/rlfhrdyd/Spring_v1.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'admin', url: 'http://tomcat-server-url')], contextPath: null, war: '**/target/hello-world.war'
            }
        }
    }
}
