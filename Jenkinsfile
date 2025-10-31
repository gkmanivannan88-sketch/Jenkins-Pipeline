pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'MAVENHOME'
    }
	environment{
		MAVEN_HOME=tool'MAVEN_HOME'
		PATH="${env.MAVEN_HOME}/bin:${env.PATH}"
	}
    stages {
        stage('Checkout') {
			steps{
            git branch: 'Jenkins01', url: 'https://github.com/gkmanivannan88-sketch/Jenkins-Pipeline.git'
        
				}
		}
        stage('Build') {
			steps{
            sh 'mvn clean install'
			}
        }
        stage('Run Application') {
			steps{
				
           			 sh 'mvn test'
			}
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












