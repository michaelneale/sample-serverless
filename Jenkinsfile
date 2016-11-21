pipeline {
	agent any	 
	
	stages {
		stage('Unit test') {
			steps {				
 			    sh 'serverless --help' // to ensure it is installed
			}
		}			
		
		stage('Integration test') {
			steps {
				sh 'serverless deploy --stage dev'
				sh 'serverless invoke --stage dev --function hello'					
			}
		}
				
		
	 	stage('Production') {
			steps {	
			    parallel (
				    'us-east-1' : {
					  sh 'serverless deploy --stage production --region us-east-1'  
					  sh 'serverless invoke --stage production --region us-east-1 --function hello'
				    },
				    'ap-southeast-2' : {
					  sh 'serverless deploy --stage production --region ap-southeast-2'  
					  sh 'serverless invoke --stage production --region ap-southeast-2 --function hello'  
				    }
				    
		            )
			}	
		}
		
		stage('Teardown') {
			steps {				
				echo 'No need for DEV environment now, tear it down'
				sh 'serverless remove --stage dev'	
			}
		}
	 
	 }
	
	
	 environment {
	 		AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
			AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
	 }

}
