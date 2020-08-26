pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
        stage(‘Upload to AWS’) {
                steps {
                withAWS(region:’us-east-1’,credentials:’fc4dee03-749d-4df9-b6b7-d808c9a7b516’) {
                    s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:’index.html’, bucket:’helloworld-pipeline’)
                }
            }    
        }
    }
}