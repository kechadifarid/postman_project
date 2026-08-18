pipeline {
    agent {
        docker {
            image 'postman/newman:latest' 
            args '-u root --entrypoint='
        }
    }

    stages {
        stage("lancer test newman")
        {
            steps{
                sh "newman run .\collection.json -e .\preprod.json "
            }
        }

    }
} 