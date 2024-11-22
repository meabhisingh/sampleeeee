
pipeline {

  agent {
   label 'worker1'
  }

     environment {
       TOKEN = credentials('vercel-token')
       VERCELPATH = 'export PATH=/home/ubuntu/.nvm/versions/node/v22.11.0/bin'
     }
  
      stages {

         stage('Check Environment Variables') {
            steps {
               sh  '$VERCELPATH && vercel -v'
            }
        }
        
         stage('Test') {
            steps {
                echo 'Testing done..'
                sh 'sudo docker -v'
                sh '$VERCELPATH && vercel -v'
            }
        }
       stage('Deploying to Vercel') {
            steps {
              echo 'Upload to Vercel'
              sh '$VERCELPATH && vercel --token $TOKEN -y --prod'
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
