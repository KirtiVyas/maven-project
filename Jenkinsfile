pipeline{
	agent any
		stages{
				stage('SCM Checkout'){steps{
						git 'https://github.com/KirtiVyas/maven-project.git'}
							}
			
				stage('Sonar Analysis'){steps{
				withSonarQubeEnv ('sonar'){
			withMaven (maven: 'LocalMaven'){
			sh 'mvn package'}
			}
				      }
					       }
				stage('install'){steps{
				withSonarQubeEnv ('sonar'){
							withMaven (maven: 'LocalMaven'){
								sh 'mvn install'}
							}
							}
							}
			stage('deploy to tomcat'){steps
			{
			sshagent(['45c07079-ce59-4923-8353-cc6f63d9622f']) {
			sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.25.90:/var/lib/tomcat/webapps'
}
			}

						 }
					}
			}
