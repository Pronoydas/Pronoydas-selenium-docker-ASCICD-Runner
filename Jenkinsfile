pipeline {
    agent any 

    stages{

        stage("Setup Grid"){
            steps{
                sh "docker-compose -f docker-selenium-grid.yml up -d "
            }
        }

        stage("Run Test"){
            steps{
                sh "docker-compose -f selenium-test.yml up"
            }
        }
    }

    post{
        always{

            sh '''
            docker-compose -f docker-selenium-grid.yml down 
            docker-compose -f selenium-test.yml down 
            '''

        }
    }
}