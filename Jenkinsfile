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
        bat 'aws s3 cp s3://my-mainbucket/D/dotnetcore22console.dll D:\\s3-artifact'
          echo "The build number is ${env.BUILD_NUMBER}"
          echo "You can also use \${BUILD_NUMBER} -> ${BUILD_NUMBER}"
          
        }
      }
    }
    stage('Unzip File'){
      steps{
        bat 'C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell Expand C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs\\dotnetcore22console\\bin\\Debug\\netcoreapp2.2\\dotnetcore22console.dll.zip C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs\\dotnetcore22console\\bin\\Debug\\netcoreapp2.2\\dotnetcore22console.dll'
      }
    }
    stage('Restart AppWebsite'){
      steps {
        bat 'iisreset'
      }
    }
    stage('Stop AppWebsite') {
      steps {
        bat 'C:\\Windows\\System32\\inetsrv\\AppCmd stop site "default2"'
      }
    }
    stage('Start AppWebsite') {
      steps {
        bat 'C:\\Windows\\System32\\inetsrv\\AppCmd start site "default2"'
      }
    }
  }
}
  

