pipeline {
  agent any
  
   stages {
     stage ('Build') {
     steps {
      sh 'printenv'
      
         }
    }
     stage ('Publish ECR') {
     steps {
       withEnv (["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_KEY_ID}","AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}","AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"]) {
            sh 'aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/h1p2m5p4'
            sh 'docker build -t ecr-demoimg .'
            sh 'docker tag ecr-demoimg:latest public.ecr.aws/h1p2m5p4/ecr-demoimg:""$BUILD_ID""'
            sh 'docker push public.ecr.aws/h1p2m5p4/ecr-demoimg:""$BUILD_ID"latest'
            }
          }
       }
     }
 }      
