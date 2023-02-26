pipeline{
    agent any
    environment{
        DOCKERHUB_USERNAME= "avatareleniyan1"
        APP_NAME="gitops-ci"
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