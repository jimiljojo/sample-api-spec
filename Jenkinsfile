pipeline {
    agent any
    environment {
        ANYPOINT_ORG_ID = 'a770f35c-9d92-4584-afb0-3c594219101b'
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
                    sh 'api-catalog-cli publish-asset -d $CATALOG_DESCRIPTOR -o $ANYPOINT_ORG_ID -a https://qax.anypoint.mulesoft.com/ --trigger=branch:master' 
                }
            }
        }
    }
}