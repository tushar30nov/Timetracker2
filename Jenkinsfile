
pipeline {

	agent any
		
	
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
		archiveArtifacts artifacts: '**/target/*.war'
            }
            
        }
        
        
        stage('Deploy') {   
        
            steps {
		    
		    deploy adapters: [tomcat9(credentialsId: 'newID', path: '', url: 'http://localhost:8081')], contextPath: 'web', war: '**/*.war'
		 
		    
            }
	}    
    }	
}
