pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
			echo "Paso 1, clean"
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
			echo "Paso 2, post"
			
        }
        stage ('Deploy to Staging'){
			echo "Paso 3, staging"
            steps {
                build job: 'deploy-to-staging'
            }
        }
    }
}