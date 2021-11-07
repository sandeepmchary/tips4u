pipeline {
    environment {
        dockerimagename = "formycore/nodeapps"
        dockerImage = ""
    }
}
agent any
stages  {
    stage('Checkout Source'){
        steps {
            git 'https://github.com/sandeepmchary/tips4u.git'
        }
    }
    stage('Build Image'){
        steps{
            script {
                dockerImage = docker.build dockerimagename
            }
        }
    }
    stage('Pushing Image'){
        environment {
            registryCredential = 'dockerlogin'
        }
        steps{
            script{
                docker.withRegistry('https://registry.hub.docker.com', 'registryCredential'){
                    dockerImage.push("latest")
                }
            }
        }
    }
}