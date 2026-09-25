pipeline {
 
  agent any

     environment {
        PATH = "/home/rajan_kumar_gautam/.nvm/versions/node/v20.20.2/bin:${env.PATH}"
          DOCKER_IMAGE = "annapurna1993/devops-gitops-app"
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
            sh'npm ci'
     }
   }
}

    stage('Docker Build') {
      steps {
        dir('app') {
          sh'docker build -t ${DOCKER_IMAGE}:${BUILD_NUMBER} -t ${DOCKER_IMAGE}:latest .'

          annapurna1993/devops-gitops-app:7 annapurna1993/devops-gitops-app:latest 
    
     }
   }
}

    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
            sh 'echo "$DOCKERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin'
             sh "docker push ${DOCKER_IMAGE}:${BUILD_NUMBER}"
              sh "docker push ${DOCKER_IMAGE}:latest"
                    sh "docker logout"
                    
          }
        }
      }
     }

       post {
        success {
          echo 'Pipeline completed successfully.'
        }
        failure {
          echo 'Pipeline failed. Check the console output.'
       }
       }
}  