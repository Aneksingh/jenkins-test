pipeline {
    agent any
       environment {
		DOCKERHUB_CREDENTIALS=credentials('anek2000')
	}

    stages(h) {
	            stage('Docker build image'){
            steps{
                sh '''	docker build -t anek2000/jenkins-test:v4 .
				'''
            }
        }
        stage('Docker-Hub Login') {

				steps {
					sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
					echo 'Login successfully'
				}
			}

			stage('Push image to Docker-Hub') {

				steps {
					sh 'docker push anek2000/jenkins-test:v4'
					echo 'Pushed successfully'
				}
			}

		stage('Docker-Hub logout') {
			steps {
				sh 'docker logout'
				echo 'Logout successfully'
			}
		}
			stage('Pipeline status') {
			steps {
				echo 'Pipeline workd successfully'
			}
		}
             
}
}
