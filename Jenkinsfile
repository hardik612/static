pipeline {
     agent any
     stages {
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'aws-static') {
                  sh 'echo "Uploading content to AWS"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-aws-static-website')
                  }
              }
         }
    }
}
