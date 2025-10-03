pipeline {
    agent any
    
   tools {
        jdk 'java-17'
        maven 'maven-3.8'
    }
    stages {
        stage('Git Checkout') {
            steps {
                echo 'Cloning the repo'
                git branch: 'main', url: 'https://github.com/Sushant-vikas/Boardgame.git'
            }
        }
        stage('Compile') {
            steps {
                echo 'maven code compilation'
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'maven code test'
                sh 'mvn test'
            }
        }
        stage('Building the package') {
            steps {
                echo 'maven code package'
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deployment of application'
                sh 'java -jar target/*.jar --server.port=8081 & '
            }
        }
    }
}
