node{
   stage('scm-checkout') {
     git 'https://github.com/krishna-sutar/Deploy-Tomcat.git'
	 }
	 stage('compile Package') {
		 steps {
			 withmaven (maven: 'LocalMaven') {
				 sh 'mvn clean compile'
			 }
		 }
	 }
	 stage('deploy to Tomcat') {
	     
		 sshagent(['tomcat-dev']) {
		     sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.17.114:/usr/share/tomcat/webapps'
	     }
	}
}
	
