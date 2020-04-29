pipeline {
    agent any
    stages {
       stage('--build--') {
            steps {
                echo '--build--'
                bat 'mvn clean package'
                //bat "docker build . -t tomcatwebapp:${env.BUILD_ID}"

            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('--deploy to staging--') {
            steps {
                echo '--deploy to staging-- pipelineAsCode-IAC'
                build job: 'deploy-to-staging'
                //bat 'mvn clean package'
                //bat "docker build . -t tomcatwebapp:${env.BUILD_ID}"
            }

        }
		stage('--deploy to Production--deploy-to-prod--') {
            steps {
				timeout(time:5, unit: 'DAYS'){
					input message: Aprove PRODUCTION Deploymrnt!1'
					}
                build job: 'deploy-to-prod'
                //bat 'mvn clean package'
                //bat "docker build . -t tomcatwebapp:${env.BUILD_ID}"
            }
			post{
				success{
			        echo '-- Success deploy to deploy-to-prod-- pipelineAsCode-IAC'
					}
				failure{
				echo '-- fail deploy to deploy-to-prod-- pipelineAsCode-IAC'
				}
				
				

			}
        }
    }

}