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
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', path: '', url: 'http://3.38.198.216:8080/')], contextPath: null, war: 'target/hello-world.war'
            }
        }
    }
}
