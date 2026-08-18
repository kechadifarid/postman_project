pipeline {
    agent {
        docker {
            image 'postman/newman:latest' 
            args '-u root --entrypoint='
        }
    }
    parameters {
        booleanParam(name: 'collection1', defaultValue: true, description: 'lancer la collection1')
        booleanParam(name: 'collection2', defaultValue: true, description: 'lancer la collection2')
    }

    stages {
        stage("lancer test newman")
        {
            steps{
                    script {
                    if((params.collection1 && params.collection2) || (!params.collection1 && !params.collection2))
                    {
                        sh "newman run ./collection1.json -e ./preprod.json "
                        sh "newman run ./collection2.json -e ./preprod.json "

                    }
                    else {
                        if(params.collection1) {
                            sh "newman run ./collection1.json -e ./preprod.json "

                        }
                        else {
                            sh "newman run ./collection2.json -e ./preprod.json "

                        }
                    }
                    }
            }
        }

    }
} 