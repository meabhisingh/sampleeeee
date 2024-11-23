
pipeline {

  agent {
   label 'worker1'
  }

     environment {
       TOKEN = credentials('vercel-token')
       VERCELPATH = 'export PATH=/home/ubuntu/.nvm/versions/node/v22.11.0/bin'
     }
  
      stages {

       stage('Deploying to Vercel') {
          when {
                expression { BRANCH_NAME == 'dev' }
            }
            steps {
              echo 'Upload to Vercel'
              sh '$VERCELPATH && vercel --token $TOKEN -y --prod'
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

    post {
        always {
            // Clean the workspace after all stages are complete
            cleanWs()
        }
    }

}
