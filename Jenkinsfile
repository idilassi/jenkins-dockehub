pipeline {
    
    agent any 
        options {
            buildDiscarder(logRotator(numTokeepStr: '5'))
        }
        environment{
            DOCKERHUB_CRENDENTIALS = crendentials ('dockerhub')
        }
        stages {
            stage('build'){
                steps {
                    bat 'docker build -t idilassi/dp-alpine:latest .'
                }

            }
            stage('login to dockerhub'){
                steps{
                    bat 'echo $DOCKERHUB_CREDENTIALS-PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                }
            }
            stage('push to dockerhub'){
                steps{
                    bat 'docker push idilassi/dp-alpine:latest'
                }
            }

        }
    post {
        always {
            bat 'docker logout'
        }
    }


    }
