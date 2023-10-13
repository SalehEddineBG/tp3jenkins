pipeline {
    agent any 
    tools { 
        maven 'maven'
    }
    stages {
        stage ("Clean up"){
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo"){
            steps {
                sh "git clone https://github.com/SalehEddineBG/tp3jenkins.git"
            }
        }
        stage ("Generate backend image") {
              steps {
                   dir("tp3jenkins"){
                      sh "mvn clean install"
                      sh "docker build -t backend ."
                  }                
              }
          }
        stage ("Run docker compose") {
            steps {
                 dir("tp3jenkins"){
                    sh "docker compose up -d"
                }                
            }
        }
    }
}
