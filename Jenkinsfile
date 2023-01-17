pipeline{
	agent any
		tools{
			maven "maven3.8.6"
		}
		stages{
			stage ('to install packages') {
           		steps {
                	bat 'mvn -Dmaven.test.failure.ignore=true install'
            		}
            	post {
                	success {
                    	junit 'target/surefire-reports/**/*.xml' 
               		}
            	}
       		}
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

                	deploy adapters: [tomcat9(credentialsId: '09f18ff8-4ba0-4f88-81be-b7d2ca9401be', path: '', url: 'http://localhost:8090/')], contextPath: null, war: '**/*.war'
           		}
			}
		}
	}
