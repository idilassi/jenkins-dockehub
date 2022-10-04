pipeline {
    
    agent any 
        
        environment{
            DOCKERHUB_CRENDENTIALS = crendentials ('dockerhub')
        }
        stages {
            stage('build'){
                steps {
                    script {
                    bat 'docker build -t idilassi/dp-alpine:latest .'
                        }
                }

            }
            stage('login to dockerhub'){
                steps{
                    script {
                    bat 'echo $DOCKERHUB_CREDENTIALS-PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                         }
                }
            }
            stage('push to dockerhub'){
                steps{
                    script {
                    bat 'docker push idilassi/dp-alpine:latest'
                        }
                }
            }

        }
    


    }
