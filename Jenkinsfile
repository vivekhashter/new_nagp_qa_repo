pipeline {
    agent any
    environment {
        PATH = "$PATH:C:/apache-maven-3.8.6/bin"
    }

 

    stages{
        stage("Get Code"){
            steps{
                git branch: 'master', changelog: false, poll: false, url: 'https://github.com/vivekhashter/new_nagp_qa_repo.git'
            }
        }
        stage('Build Code'){
            steps{
                bat 'mvn clean test'
            }
        }
        stage('Sonar Qube'){
            steps{
                withSonarQubeEnv('SonarqubeServer'){
                    bat 'mvn clean verify sonar:sonar'
                }
            }
        }
    }
}
