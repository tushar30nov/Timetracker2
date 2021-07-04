
pipeline {

	agent any
	environmnet{
		url = 'http://localhost:8082'
		contextPath = 'web'
	
    stages {
    
    	stage('Checkout')
    	{
    		steps{
    			git 'https://github.com/tushar30nov/Timetracker2.git'
			
		echo "Checkout done"
    		}
    	
    	}
	    
	  stage('Test') {
            steps {
                sh "mvn clean test"
		 echo "Test completed"
            }
            
        }  
	    
	    
        stage('Build') {   
        
            steps {
             sh "mvn package"
             echo "Build completed"
            }
            
        }
        
        
        stage('Deploy') {   
        
            steps {
            deploy adapters: [tomcat9(credentialsId: 'admin1', path: '', url: 'http://localhost:8082')], contextPath: 'web', war: 'time-tracker-web-0.5.0-SNAPSHOT.war'
		 
            }
	}    
    }	
}
