pipeline {
    agent any
	
    tools
    {
       maven "Maven"
       dockerTool "docker"
    }
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/devops4solutions/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

    stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
               
               
          }
        }
     
 
      
    stage('Run Docker container on Jenkins Agent') {
             
            steps 
			{
                sh 'docker run -d -p 8003:8080 samplewebapp'
 
            }
        }
    }
}
    
