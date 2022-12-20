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
            sh 'aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 816911947835.dkr.ecr.us-east-2.amazonaws.com'
            sh 'docker build -t jenkin-pipeline-build-demo .'
            sh 'docker tag jenkin-pipeline-build-demo:latest 816911947835.dkr.ecr.us-east-2.amazonaws.com/jenkin-pipeline-build-demo:latest'
            sh 'docker push 816911947835.dkr.ecr.us-east-2.amazonaws.com/jenkin-pipeline-build-demo:latest'
            }
          }
       }
     }
 }      
