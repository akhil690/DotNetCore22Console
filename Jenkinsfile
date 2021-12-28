pipeline {
  agent any
  environment {
    awscli = "C:\\Program Files\\Amazon\\AWSCLIV2\\awscli"
    appcmd= "C:\\Windows\\System32\\inetsrv"
  }
  stages {
    stage('S3 Download') {
      steps {
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'c7404c17-3b93-4e2d-8b86-4f1a2ce6bdb2', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
        {
        bat 'aws s3://my-mainbucket/D/dotnetcore22console.dll D:\s3-artifact'
        }
      }
    }
    stage('restart AppWebsite'){
      steps {
        bat 'iisreset'
      }
    }
    stage('stop AppWebsite') {
      steps {
        bat 'C:\\Windows\\System32\\inetsrv\\AppCmd stop site "default2"'
      }
    }
    stage('start AppWebsite') {
      steps {
        bat 'C:\\Windows\\System32\\inetsrv\\AppCmd start site "default2"
      }
    }
  }
}
  

