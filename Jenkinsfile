pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Dockernandha')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git  'https://github.com/mrmeowboi/node-redis-mongo.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t mrmeowboi/node:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Push') {

			steps {
				sh 'docker push mrmeowboi/node:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
