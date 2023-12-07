pipeline {
	agent any
	
	tools{
		maven "Maven"
       		dockerTool "docker"
    	}
     	stages {
      		stage('checkout') {
           	    steps {
             
               		git branch: 'main', url: 'https://github.com/ihab-soufiane/webapp.git'
             
         		}
        }
   	stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

    	stage('Docker Build ') {
            steps {
              
                sh 'docker build -t webApp:v1 .' 
               
               
          }
        }
     
 
      
    	stage('Run Docker container on Jenkins Agent') {
             
            steps 
			{
                sh 'docker run --name ihab/webApp -d -p 8003:8080 webApp:v1'
 
            }
        }
    }
}
    
