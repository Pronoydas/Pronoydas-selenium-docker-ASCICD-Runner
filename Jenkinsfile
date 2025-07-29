pipeline {
    agent any 

    parameters {
       choice choices: ['chrome', 'firefox'], description: 'Select Browser', name: 'BROWSER'
        }


    stages{

        stage("Setup Grid"){
            steps{
                sh "docker-compose -f docker-selenium-grid.yml up --scale=${params.BROWSER}=1  -d "
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