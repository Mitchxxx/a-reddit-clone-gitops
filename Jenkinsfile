pipeline {
  agent any
  environment {
    APP_NAME = "reddit-clone-app"
  }
  stages {
    stage('Clean Workspace'){
      steps{
        cleanWs()
      } 
    }
    stage('Checkout from Git'){
      steps{
         git branch: 'main', credentialsId: 'github', url: 'https://github.com/Mitchxxx/a-reddit-clone-gitops'
      } 
    }
    stage('Update deployment tags'){
      steps{
         sh """
             cat deployment.yaml
             sed -i 's/${APP_NAME}.*/${APP_NAME}:${IMAGE_TAG}/g' deployment.yaml
             cat deployment.yaml
            """
      } 
    }
    stage('Push updated Deployment repo'){
      steps{
         sh """
             git config --global user.name "Mitchxxx"
             git config --global user.email "megboko@gmail.com"
             git add deployment.yaml
             git commit -m "Updated Deployment Manifest"
           """
        withCredentials([gitUsernamePassword(credentialsId: 'github', gitToolName: 'Default')]) {
          sh "git push https://github.com/Mitchxxx/a-reddit-clone-gitops main"
        }
      } 
    }
  }
}
