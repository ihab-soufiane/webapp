pipeline {
	agent any
	
	tools{
		maven "Maven"
       		dockerTool "docker"
    	}
     	stages {
      		stage('checkout') {
           	    steps {
             
               		git branch: 'main', credentialsId: '123', url: 'https://github.com/ihab-soufiane/webapp.git'
             
         		}
        }
   	stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

    	stage('Docker Build ') {
            steps {
		script{
                     withDockerRegistry(credentialsId: 'b17da05a-467c-43d8-a57f-166c83749f52') toolName: 'docker') {
                     sh 'docker build -t webapp:v1 .' 
		}
}
               
               
               
          }
        }
     
 
      
    	stage('Run Docker container on Jenkins Agent') {
             
            steps 
			{
                sh 'docker run --name ihab/webapp -d -p 8003:8080 webapp:v1'
 
            }
        }
    }
}
    
