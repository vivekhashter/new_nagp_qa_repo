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
                withSonarQubeEnv('SonarQube'){
                    bat 'mvn clean verify sonar:sonar -Dsonar.projectKey=newwebapp  -Dsonar.projectName="newwebapp" -Dsonar.host.url=http://localhost:9000  -Dsonar.token=sqp_a576237b0c840c4b4bc73b0781d55faa36911e8b'
                }
            }
        }
    }
}
