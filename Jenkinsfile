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
					deploy adapters: [tomcat10(credentialsId: 'tomcat', path: '', url: 'http://localhost:9090/')], contextPath: 'devOpsWeb', war: '**/*.war'
				}
			}
		}
	}
