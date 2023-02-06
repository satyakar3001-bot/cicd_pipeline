pipeline{
    agent any
    tools{
        maven 'maven_3_5_0'
    }
    stages{
        stage("Build Maven Project"){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/satyakar3001-bot/cicd_pipeline.git']])
                bat 'mvn clean install'
                
            }
        }
        stage("build docker image"){
            steps{
                script{
                    bat 'docker build -t satu/devops-integration .'
                }
            }
        }
        stage("Push image to hub"){
            steps{
                script{
                    withCredentials([string(credentialsId: 'docker-hubpassword2', variable: 'dockerhubpassword2')]) {
                    bat 'docker login -u satyakar3001 -p dockerhubpassword'
}

                    bat 'docker images'
                    bat 'docker ps -a'
                }
            }
        }
    }
}
