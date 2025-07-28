pipeline {
    agent any 

    stages{

        stage("Run Docker Compose"){
            steps{
                sh "docker-compose up"
            }
        }

        stage("Clean Up"){
            steps{
                sh "docker-compose down"
            }
        }
    }
}