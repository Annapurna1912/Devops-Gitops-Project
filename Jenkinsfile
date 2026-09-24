pipeline {
 
  agent any

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
