pipeline {
    agent any
    
	triggers {
		pollSCM('* * * * *')
	}

    stages {
        stage('hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Checkout') {
            steps {
                git branch: 'main', 
                url: 'https://github.com/milkyway971/source-maven-java-spring-hello-webapp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }

    }
}
