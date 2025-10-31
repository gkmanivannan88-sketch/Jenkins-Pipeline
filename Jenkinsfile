pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            git branch: 'main' url:https://github.com/gkmanivannan88-sketch/Jenkins-Pipeline.git
        }
        stage('Build') {
            sh 'mvn clean install'
        }
        stage('Run Application') {
            sh 'mvn test'
        }
        stage('Test') {
            // write your logic here
            post {
                success {
                    junit 'target/surefire-reports/*.xml'
					echo 'Build and Tests Passed Successfully'
                }
				failure {
                    junit 'target/surefire-reports/*.xml'
					echo 'Build and Tests failed'
                }
            }
        }
    }
}

