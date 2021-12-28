pipeline {
  agent any
  environment {
    awscli = "C:\\Program Files\\Amazon\\AWSCLIV2\\awscli"
    envars= 
      appcmd = "C:\\Windows\\System32\\inetsrv"
  }
  stages{
    stage('Env Variables'){
      steps{
        bat 'set'
      }
    }
    stag{
      steps{
                echo "The build number is ${env.BUILD_NUMBER}"
                echo "You can also use \${BUILD_NUMBER} -> ${BUILD_NUMBER}"
            }
  }
  stages {stage('S3 Download') {
    steps {
      withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'c7404c17-3b93-4e2d-8b86-4f1a2ce6bdb2', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
      {
        bat 'aws s3://my-mainbucket/D/dotnetcore22console.dll D:\s3-artifact'
      }
    }
  }
         }
  

