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

        
        stage('build docker image'){
            steps{
                bat 'docker build --no-cache -t devopsproject -f Dockerfile .'
            }
        }
        

        stage('dockerhub login'){
            steps{
                bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
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