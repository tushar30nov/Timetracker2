
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
		    
		    deploy adapters: [tomcat8(credentialsId: 'admin123', path: '', url: 'http://localhost:8082')], contextPath: 'web', onFailure: false, war: '**/*.war'
		    
            }
	}    
    }	
}
