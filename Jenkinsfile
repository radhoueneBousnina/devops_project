pipeline{
    agent any
    environment{
        DOCKERHUB_CREDENTIALS = credentials('dh_cred')
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
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            } 
        }
        
        stage('build docker image'){
            steps{
                sh 'docker build --no-cache -t radhouene03/devopsproject:0.1 -f Dockerfile .'
            }
        }
        

        stage('push'){
            steps{
                sh 'docker push radhouene03/devopsproject:0.1'
            }
        }

        stage('logout'){
            steps{
                sh 'docker logout'
            }
        }


    }
}