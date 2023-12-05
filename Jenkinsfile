pipeline {
    agent {
      label "jenkins-node"
    }
    
	triggers {
		pollSCM('* * * * *')
	}

    stages {
        stage('Hello') {
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
                sh 'mvn clean package -DskipTests=true'
            }
        }
		stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', path: '', url: 'http://3.38.198.216:8080/')], contextPath: null, war: 'target/hello-world.war'
            }
        }
    }
}
