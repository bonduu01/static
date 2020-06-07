pipeline {
  agent any
  stages {
         stage('Upload to AWS') {
              steps {
                  withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-static', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
                  {
                       //s3Upload consoleLogLevel: 'INFO', pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'bonduu-static-jenkins-pipeline'
                       s3Upload consoleLogLevel: 'INFO', dontSetBuildResultOnFailure: false, dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'bonduu-static-jenkins-pipeline', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-west-2', showDirectlyInBrowser: false, sourceFile: 'index.html', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'bonduu-static-jenkins-pipeline', userMetadata: []
                  }
              }
         }
             stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
    }
  }
