pipeline{
    agent any
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker')
    }
    stages {
        stage('clone'){
            steps {
                git branch : 'main', 
                url: 'https://github.com/radhoueneBousnina/devops_project.git'
            }
        }

        stage('dockerhub login'){
            steps{
                withCredentials([usernamePassword(credentialsId:'docker', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                    bat 'docker login -u $USERNAME -p $PASSWORD'
                }
            } 
        }

        stage('build docker image'){
            steps{
                bat 'docker build --no cache -t devopsproject -f Dockerfile .'
            }
        }

        stage('push'){
            steps{
                bat 'docker push radhouene03/devopsproject'
            }
        }

        stage('logout'){
            steps{
                bat 'docker logout'
            }
        }


    }
}