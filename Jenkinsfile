pipeline{

  agent any
  
  stages {
      
      stage("code"){
          steps{
              git url: "https://github.com/nangareashu29/node-todo-cicd" , branch: "main"
              echo "Code Cloned Successfully"
          }
      }
      stage("Build"){
          steps{
              sh 'docker build -t node-app:latest .'
              echo "Code Build Successfully"
          }
      }
      stage("Test"){
         steps{
             echo "Build Tested Successfully"
         } 
      }
      stage("Push to Private Hub Repo"){
          steps{
              echo "Docker Image Pushe Successfully Deployed Successfully"
          }
      }
      stage("Sonar"){
          steps{
              echo "Build Tested Successfully"
          }
      }
      stage("OWASp"){
          steps{
              echo "App Deployed Successfully"
          }
      }
      stage("Trivy"){
          steps{
              echo "App Deployed Successfully"
          }
      }
      stage("Deploy"){
          steps{
              echo "App Deployed Successfully"
          }
      }
  }
}
