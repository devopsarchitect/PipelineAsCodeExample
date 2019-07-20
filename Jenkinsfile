pipeline {
    agent any
    stages {
       stage('--build--') {
            steps {
                echo '--build--'
                bat 'mvn clean package'
                //bat "docker build . -t tomcatwebapp:${env.BUILD_ID}"

            }
        }
        post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }

    }
}
