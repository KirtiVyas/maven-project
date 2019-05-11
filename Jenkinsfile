pipeline{
	agent any
		stages{
				stage('SCM Checkout'){steps{
						git 'https://github.com/KirtiVyas/maven-project.git'}
							}
				stage('compile source code'){steps{
							withMaven (maven: 'LocalMaven'){
								sh 'mvn compile'}
							}
												}
			 	stage('test'){steps{
							withMaven (maven: 'LocalMaven'){
								sh 'mvn test'}
							}
								}
				stage('package'){steps{
							withMaven (maven: 'LocalMaven'){
								sh 'mvn package'}
							}
									}
					stage('install'){steps{
							withMaven (maven: 'LocalMaven'){
								sh 'mvn install'}
							}
							}
					}
			}
