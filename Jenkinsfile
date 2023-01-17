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

                			deploy adapters: [tomcat9(credentialsId: '6d7c744f-4254-42d8-84c9-f2ad5a41b79d', path: '', url: 'http://localhost:8090')], contextPath: null, war: '**/*.war'
           			 }
			}
		}
	}
