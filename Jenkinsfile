pipeline{
    agent any
    environment{
        IMAGE_NAME = "dotnetApp"
        IMAGE_TAG = '${BUILD_NUMBER}'
    }
    stages{
        stage("checkout"){
            steps{
                git url
            
            }
        }
        stage("docker build"){
            steps{
                sh '''
                    docker build -t $IMAGE_NAME:$IMAGE_TAG .

                '''
            }
        }
        stage("check images"){
            steps{
                sh '''
                    docker images

                '''
            }
        }
    }

}
