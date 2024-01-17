pipeline {
  agent any
  environment {
    APP_NAME = "reddit-clone-app"
  }
  stages {
    stage(Clean Workspace){
      step{
        cleanWs()
      } 
    }
    stage(Checkout from SCM){
      step{
         git branch: 'main', credentialsId: 'github', url: '
      } 
    }
  }
}
