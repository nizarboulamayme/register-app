pipeline {
	agent { label 'Jenkins-Agent' }
	tools {
		jdk 'Java17'
		maven 'Mavenggççàç'
	}
	stages{
		stage("Cleanup Workspace"){
			steps {
				cleanWs()
			}
		}
		stage("Checkout from SCM"){
			steps {
				git branch: 'main' , credentialsId: 'github' , url: 'https://github.com/nizarboulamayme/register-app'
			}
		}
		stage("Build App"){
			steps {
				sh "mvn clean package"
			}
		}
		stage("Test App"){
			steps {
				sh "mvn test"
			}
		}
		
		stage("SonarQube Analysis"){
           		steps {
	           		script {
		        		withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token') { 
                        			sh "mvn sonar:sonar"
					}
				}
			}
		}
					
						
		        
	}
}
	
