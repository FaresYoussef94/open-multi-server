pipeline{
    agent any

    environment {
        DOCKER_REPO = 'faresyoussef'
        DOCKER_IMAGE = 'mutli-server'
    }

    stages{

        stage('Build'){
            steps{
                echo 'Building ...'
            }
        }

        stage('Test'){
            steps{
                echo 'Testing ...'
            }
        }

        stage('Dockerizing'){
            steps{
                echo("Creating Docker image for build: $BUILD_NUMBER")
                sh 'docker build -t ${DOCKER_REPO}/${DOCKER_IMAGE} .'
                echo("Pushing docker image to the repository")
                sh 'docker push ${DOCKER_REPO}/${DOCKER_IMAGE}'
            }
        }

        stage('Deploy'){
            steps{
                echo("Deploying to Kubernetes cluster")
                sh 'kubectl delete -f kubernetes/'
                sh 'kubectl apply -f kubernetes/'
            }
        }

    }

}