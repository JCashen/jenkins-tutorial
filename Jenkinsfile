pipeline{
        agent any
        stages{
            stage('Clone repo'){
                steps{
                    sh "git clone https://gitlab.com/qacdevops/chaperootodo_client"
                }
            }
            stage('download docker'){
                steps{
                    sh "curl https://get.docker.com/ | sudo bash"
                        sh "sudo usermod -aG docker $(whoami)"   
                }
            }
             stage('download compose'){
                 steps{
                     sh "sudo curl -L "https://github.com/docker/compose/releases/download/$%7Bversion%7D/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose"
                     sh "sudo chmod +x /usr/local/bin/docker-compose"
                  }
              }
              stage('deploy'){
                  steps{
                     sh"sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d"
                  }
              }
        }
                     
}
