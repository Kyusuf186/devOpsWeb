pipeline{
	agent any
		tools{
			maven "maven3.8.6"
		}
		stages{
			stage("build"){
				steps{
					bat 'mvn clean package'
				}
				post{
					success{
						echo "Archiveing the Artifacts"
						archiveArtifacts artifacts: '**/target/*.war'
					}
				}
			}
			stage("deploy"){
				 steps{

                			echo "Deployment"
           			 }
			}
		}
	}
