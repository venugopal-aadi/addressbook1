pipeline {
    agent any
    
    
    stages {
        stage('Checkout') {
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/venugopal-aadi/addressbook1.git']]])
            }
        }
        stage('Compile') {
            steps {
            sh 'mvn clean compile'
            }
        }  
        stage('Test') {
            steps {
            sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
            sh 'mvn clean package'
            }
        } 
       stage('Deployment') {
	   steps {
		sh 'sshpass -p staragile scp target/addressbook.war staragile@172.31.32.161:/home/staragile/apache-tomcat-9.0.85/webapps/prodenv/'
	} 
    }
}
}
