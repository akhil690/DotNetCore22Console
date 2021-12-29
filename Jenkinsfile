pipeline {
agent any

environment {

dotnet='C:\\Program Files (x86)\\dotnet'
awscli = 'C:\\Program Files\\Amazon\\AWSCLIV2\\awscli'
}
stages {
    stage('Checkout') {
        steps {
            git 'https://github.com/akhil690/DotNetCore22Console.git'
        }
    }
    stage('Restore') {
        steps {
            bat 'dotnet restore C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs'
            }
        
    }
    stage('Clean') {
        steps {
            bat 'dotnet clean C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs'
        }
    }
    stage('Build') {
        steps {
            bat 'dotnet build C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs --configuration Release'
        }
    }
     stage('Unit Test') {
         steps {
             bat 'dotnet test C:\\Windows\\system32\\config\\systempr{}.ofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs'
         }
     }
      stage('Publish') {
          steps {
              bat 'dotnet publish C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs'
         }
     }
      stage('Versioning') {
          steps{
              cp s3://my-mainbucket/D/dotnetcore22console.dll${Multi-Branch-Pipeline}.$
              {env.build.number}
         }
     }
      stage('Upload'){
          steps {
              withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'c7404c17-3b93-4e2d-8b86-4f1a2ce6bdb2', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
              {
                  bat 'aws s3 ls'
                  bat 'aws s3 cp C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs\\dotnetcore22console\\bin\\Debug\\netcoreapp2.2\\dotnetcore22console.dll  s3://my-mainbucket/D/dotnetcore22console.dll'
              }
                
            }
}
}
}
