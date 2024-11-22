
pipeline {

  agent any

      environment {
        PROJECT_NAME = 'myapp'
        DOCKER_IMAGE ="${PROJECT_NAME}:${params.dockerImageVersion}"
        AWS_REGION="ap-southeast-1" 
        ECS_CLUSTER = "arn:aws:ecs:ap-southeast-1:891376965446:cluster/DevCluster"
        ECS_SERVICE = "arn:aws:ecs:ap-southeast-1:891376965446:service/DevCluster/myapp-service"
      
    }

      stages {

         stage('Test') {
            steps {
                echo 'Testing..'
            }
        }

       stage('Deploying to Vercel') {
          when{
                expression { BRANCH_NAME == 'dev' }
            }
            steps {
              echo 'Upload to Vercel'
            }
        }

       stage('Deploying to ECS') {
          when{
                expression { BRANCH_NAME == 'master' }
            }
            steps {
              echo 'Upload to ECS'
            }
        }
      }

}
