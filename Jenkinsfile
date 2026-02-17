pipeline{
	agent any 

	stages{
		stage('Clone Repo'){
			steps{
				git 'https://github.com/krishnachandra1998/jenkins_docker_deployment.git'

			}
		}
		
		stage('Build Docker Image'){
			steps{
				sh 'docker build -t jenkins_docker_deployment:latest .'
			}
		}
		stage('Deploy Container') {
            steps {
                sh '''
                docker stop my-website || true
                docker rm my-website || true
                docker run -d -p 80:80 --name jenkins_docker_deployment jenkins_docker_deployment:latest
                '''
            }
        }
	}
}

