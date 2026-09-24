pipeline {
 
  agent any

     environment {
        PATH = "/home/rajan_kumar_gautam/.nvm/versions/node/v20.20.2/bin:${env.PATH}"
     } 

     stages {

         stage('Checkout') {
            steps {
               checkout scm
   }
}


      stage('Install Dependencies') {
        steps {
          dir('app') {
            sh'npm install'
     }
   }
}

    stage('Docker Test') {
      steps {
        sh'docker images devops-gitops-app:jenkins'
    
     }
   }
}


  post {
   success {
    echo 'Pipeline completed successfully!'
   }


   failure {
    echo 'Pipeline failed. Check the console output.'

      }
    }
}
