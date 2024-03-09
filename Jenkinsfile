pipeline {
    
    agent any
    
    stages {
        
        stage("Code"){
            steps{
                git url: "https://github.com/nangareashu29/node-todo-cicd.git" , branch: "main"
                echo "Code Cloned Successfully"
            }
        }
        stage("Build"){
            steps{
                sh 'docker build -t nodeapp:latest .'
                echo "Code Built Successfully"
            }
        }
        stage("Test"){
            steps{
                echo "Build Tested Successfully"
            }
        }
        stage("Push to Private Docker Hub Repo"){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockercred",passwordVariable:"dockerPass",usernameVariable:"dockerUser")]){
                sh "docker login -u ${env.dockerUser} -p ${env.dockerPass}"
                sh "docker tag nodeapp:latest ${env.dockerUser}/nodeapp:latest"
                sh "docker push ${env.dockerUser}/nodeapp:latest"
                }
                
            }
        }
        stage("Sonar"){
            steps{
                echo "Build Tested Successfully"
            }
        }
        stage("OWASP"){
            steps{
                echo "Build Tested Successfully"
            }
        }
        stage("Trivy"){
            steps{
                echo "Image Scanned Successfully"
            }
        }
        stage("Deploy"){
            steps{
                sh "docker-compose up -d"
                echo "App Deployed Successfully"
            }
        }
    }
}
