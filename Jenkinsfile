pipeline{
    agent any
    environment{
        DOCKERHUB_USERNAME= "avatareleniyan1"
        APP_NAME="gitop"
        IMAGE_TAG="${BUILD_NUMBER}"
        IMAGE_NAME="${DOCKERHUB_USERNAME}" + "/" + "${APP_NAME}"
        REGISTRY_CREDS="dockerhubID"
    }
    stages{
        stage('Clean workspace area'){
            steps{
                script{
                    cleanWs()
                }
            }
        }
        stage ('Check-Git-Secrets') {
		    steps {
                script{
                    sh 'rm trufflesecurity/trufflehog:latest || true'
                    sh 'docker run --rm -t -v "$PWD:/pwd" trufflesecurity/trufflehog:latest github --repo https://github.com/avatareleniyan1/gitops-ci.git --debug > trufflehog'
		            sh 'cat trufflehog'

               }
	         
	       }
        }
        stage('Git Checkout SCM'){
            steps{
                script{
                    git credentialsId: 'gitops-ci',
                    url: 'https://github.com/avatareleniyan1/gitops-ci.git',
                    branch: 'main'
                }
            }
        }
    }
}