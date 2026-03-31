pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/Aditya09977/devops-final', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                dir('Student-Feedback-Website-main') {
                    bat 'mvn clean install -DskipTests'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('Student-Feedback-Website-main') {
                    bat 'mvn test'
                }
            }
        }
    }

    post {
        always {
            junit 'Student-Feedback-Website-main/target/surefire-reports/*.xml'
        }
    }
}
