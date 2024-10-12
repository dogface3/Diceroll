pipeline {
    agent any
    tools {
        maven 'Maven3'  // Ensure Maven is installed
        jdk 'JD'     // Ensure JDK is installed
    }
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/dogface3/Diceroll'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Run Unit Tests') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'  // Capture test reports
                }
            }
        }
        stage('Code Coverage Report') {
            steps {
                bat 'mvn jacoco:report'
            }
            post {
                always {
                    jacoco execPattern: 'target/jacoco.exec'
                }
            }
        }
    }
}


