
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
                echo $PATH
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
