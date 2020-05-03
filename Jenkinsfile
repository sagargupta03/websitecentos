

// Script //
 
node
{
  agent { label 'staging'}
  // possible options agent any, none , label	
  def app
	
        stage('Clone Repository') {

	echo 'Cloning the repository to our workbook....'
        checkout scm
        }

	stage('Build Image') {
	echo 'This builds the actual image....'
	app = docker.build("sagargupta03/website4maythird")
	}

        stage('Test Image') {
        app.inside{
        echo 'Test passed....'
                  }
	}

        stage('Push Image') {
        echo 'Pushing image to Docker Hub....'
	echo 'SG-docker-hub is name of Docker credential...'

        docker.withRegistry('https://registry.hub.docker.com', 'SG-docker-hub')
	 {
        app.push("${env.BUILD_NUMBER}")
        app.push("latest")
	 }	
	/*echo ${env.BUILD_NUMBER}*/

	}
}
