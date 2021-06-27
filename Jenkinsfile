
pipeline {

	agent any
	
    stages {
    
    	stage('Checkout')
    	{
    		steps{
    			git 'https://github.com/tushar30nov/Timetracker2.git'
    		}
    	
    	}
        stage('Build') {   
        
            steps {
             sh "mvn clean package"
               
            }
            
        }
        stage('Test') {
            steps {
                sh "mvn clean test"
            }
            
        }
        
        stage('Deploy') {   
        
            steps {
            sh "mvn clean deploy"
            archiveArtifacts artifacts: '**/target/*.war'
               
            }
			}    
    }	
}
