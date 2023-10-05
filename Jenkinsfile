pipeline {
    agent any
    stages {
        stage('Greeting') {
            steps {
                sh ''' 
                echo "Hello, Jenkins is working"
                '''
            }
        }
      stage('Build Images') {
            steps {
                sh ''' 
                echo "Hello, Starting the image build process"

                # BUILDING EACH IMAGE IN TURN
                # LATEST PLUS A VERSION NUMBERED IMAGE

                docker build -t ethnicbadger/duo-flask:latest .
                docker build -t ethnicbadger/duo-flask:${BUILD_NUMBER} .
            
                '''
            }
        }
stage('Push Images') {
            steps {
                sh ''' 
                echo "Hello, Starting to push the images to DockerHub"

                # PUSH THE NEW IMAGES TO DOCKER HUB

                docker push ethnicbadger/duo-flask:latest
                docker push ethnicbadger/duo-flask:${BUILD_NUMBER}
                '''
            }
        }

stage('clean up Jenkins') {
            steps {
                sh ''' 
                echo "Hello, Starting clean up of Jenkins"

                docker rmi ethnicbadger/duo-flask:latest
                docker rmi ethnicbadger/duo-flask:${BUILD_NUMBER}
                '''
            }
        }

        stage('Deploy Containers') {
            steps {
                sh ''' 
                echo "Hello, Jenkins is still working"

                # NOW WE'RE GOING TO DEPLOY THE CONTAINERS BASED ON THE IMAGES GENERATED

                kubectl
                
                '''
            }
        }
        
    }
}
