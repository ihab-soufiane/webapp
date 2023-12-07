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
                     withDockerRegistry(credentialsId: '9177bc4c-188e-4f08-aabd-0fcfba1d9c37', toolName: 'docker') {
		     }
                     sh 'docker build -t webapp:v1 .' 
		}
       }
               
               
               
          }
        
     
 
      
    	stage('Run Docker container on Jenkins Agent') {
             
            steps {
                sh 'docker run -d -p 8003:8080 webapp:v1'
            }
        }
    }
}
    
