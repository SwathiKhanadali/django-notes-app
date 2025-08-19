@Library('Shared') _
pipeline{
    agent { label 'lando'}
    
    stages{
        stage("Hello")
           {
            steps{
                script
                  {
                    hello()
                  }
                }
                       }
        stage("Code clone"){
            steps{
            script{
                clone("https://github.com/SwathiKhanadali/django-notes-app.git", "main")
            }
                 }
                          }
        stage("Code Build"){
            steps{
                script{
            docker_build("notes-app","latest", "swathishrikantkhanadali3")
                      }
        }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                docker_push("notes-app", "latest", "swathishrikantkhanadali3")
            }
            }
        }
        stage("Deploy"){
            steps{
                echo"This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
        
    }
}
