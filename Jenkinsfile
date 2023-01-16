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

                			deploy adapters: [tomcat9(credentialsId: '1358c8b2-6f9e-4c4b-8ba7-c3b89c952448', path: '', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
           			 }
			}
		}
	}
