pipeline {
    agent any

//	tools {
//		jdk 'jdk8'
//	}
//	environment {
//		M2_INSTALL = "/usr/bin/mvn"
//	}

    stages {
        stage('Clone-Repo') {
	    	steps {
                sh 'mvn compile'
	    	}
        }

        stage('Build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
		
        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deployment') {
            steps {
                sh 'sshpass -p "staragile" scp target/gamutkart.war staragile@172.31.3.224:/home/staragile/apache-tomcat-9.0.85/webapps'
            }
        }
    }
}
