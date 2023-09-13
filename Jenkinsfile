pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
                echo 'checksource code'
				git 'https://github.com/teluguhackerforfree/maven.git'
            }
        }
		stage('compile') {
            steps {
                echo 'compile code'
				sh 'mvn compile'
            }
        }
		stage('artifact') {
            steps {
                echo 'generate artifact'
				sh 'mvn package'
            }
        }
		stage('deploy') {
            steps {
                echo 'deploy artifact'
				deploy adapters: [tomcat9(credentialsId: 'tomcat-credential', path: '', url: 'http://100.25.151.8:8081/')], contextPath: 'dev', war: '**/*.war'
				 }
				
        }
    }
}
