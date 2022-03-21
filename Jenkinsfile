pipeline {
    agent any
    environment {
        ANYPOINT_ORG_ID = 'ac6d936c-c476-4e60-8007-d00a4f2bff8c'
        CATALOG_DESCRIPTOR = './descriptor.yaml' 
     }
     stages {
    
        stage('API Cataloging') {
            steps {
                 withCredentials([
                    usernamePassword(credentialsId: 'my-anypoint-creds',
                    usernameVariable: 'ANYPOINT_USERNAME',
                    passwordVariable: 'ANYPOINT_PASSWORD')
                ]) {
                    sh 'api-catalog publish-asset -d $CATALOG_DESCRIPTOR -o $ANYPOINT_ORG_ID -a https://anypoint.mulesoft.com --trigger=branch:master' 
                }
            }
        }
    }
}