
pipeline {

  agent any

     environment {
       TOKEN = credentials('vercel-token')
     }
  
      stages {
         stage('Test') {
            steps {
                echo 'Testing done..'
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
