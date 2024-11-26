pipeline {
    agent any 
    tools { 
        maven 'maven'
        nodejs 'node'
    }
    stages {
        stage ("Clean up"){
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo"){
            steps {
                sh "git clone https://github.com/alahammami2/Fullstack_Jenkins.git "
            }
        }
        stage ("Generate frontend image") {
            steps {
                 dir("Fullstack_Jenkins/angular-app"){
                    sh "docker build -t angular-app ."
                }                
            }
        }
        stage ("Generate backend image") {
              steps {
                   dir("Fullstack_Jenkins/springboot/app"){
                      sh "mvn clean install"
                      sh "docker build -t springboot-app ."
                  }                
              }
          }
        stage ("Run docker compose") {
            steps {
                 dir("Fullstack_Jenkins"){
                    sh " docker-compose up -d"
                }                
            }
        }
    }
}






