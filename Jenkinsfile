pipeline {
    agent any

    stages {
        stage('Clone SCM') {
            steps {
                echo 'cloning Repository '
				git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
		
		  stage('Build artifact') {
            steps {
                echo 'Buidling war file'
				sh 'mvn clean install '
				
            }
        }
		
		  stage('Deploy to Tomcat') {
            steps {
                echo 'Deploying appplication to tomcat'
				deploy adapters: [tomcat9(credentialsId: 'batch6', path: '', url: 'http://3.95.64.115:8080/')], contextPath: 'gameoflifewebapplication', war: '**/*.war'
				
            }
        }  
		
		
    }
}
