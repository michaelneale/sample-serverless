pipeline {
	 agent label:'master'
	 stages {
	 	stage('deploy') {
		 	withCredentials([[$class: 'UsernamePasswordMultiBinding', 
		 		    credentialsId: 'amazon',
	                            usernameVariable: 'AWS_ACCESS_KEY_ID', 
	                            passwordVariable: 'AWS_SECRET_ACCESS_KEY']]) {
			      sh 'serverless deploy'	                            	
	            	}
		}
	 
	 }

}
