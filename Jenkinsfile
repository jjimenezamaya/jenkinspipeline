pipeline {
	agent any

	parameters {
		string(name:'tomcat_dev', defaultValue: '35.166.210.154', description: 'Staging Server')
		string(name:'tomcat_prod', defaultValue: '34.209.233.6', description: 'Production Server')
	}

	triggers {
		pollSCM('* * * * *')
	}

	stage ('Deployments') {
		
		/*Dice a Jenkins que puede ejecutar ambas acciones en paralelo*/
		
		parallel{ 
			stage('Deploy to Staging'){
				steps{
					sh "scp -i /home/jenkins/tomcat-demo.pem **/target/*.war"
				}
			}

			stage('Deploy to Production'){
				steps{
					sh "scp -i /home/jenkins/tomcat-demo.pem **/target/*.war"
				}
			}
		}
	}
}
