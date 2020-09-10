pipeline {
     
     agent any
     stages {
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }  
          
         stage('Security Scan') {
              steps { 
                 aquaMicroscanner imageName: 'alpine:latest', notCompleted: 'exit 1', onDisallowed: 'fail'
              }
         }         
          
         stage('Upload to AWS') {
              steps {
                  sh '''
                    echo "Uploading index.html to AWS S3"
                    aws s3 cp index.html s3://udacity-aws-static-website/
                '''
                  }
         }

    }
}
