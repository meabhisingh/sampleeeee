
pipeline {

  agent {
   label 'worker1'
  }

     environment {
       TOKEN = credentials('vercel-token')
     }
  
      stages {

         stage('Check Environment Variables') {
            steps {
               sh  'export PATH=$PATH:/home/ubuntu/.nvm/versions/node/v22.11.0/bin/vercel && vercel -v'
            }
        }
        
         stage('Test') {
            steps {
                echo 'Testing done..'
                sh 'sudo docker -v'
                sh 'vercel -v'
            }
        }
       stage('Deploying to Vercel') {
            steps {
              echo 'Upload to Vercel'
              sh 'vercel --token $TOKEN -y --prod'
            }
        }
      }

}
