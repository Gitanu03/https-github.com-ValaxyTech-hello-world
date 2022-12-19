pipeline {
  agent any
  stages {
    stage {'Build'} {
      steps {
        sh 'printenv'
        
        }
      }
      stage {'Publish ECR'} {
        steps {
          withEnv (["AWS_ACCESS_KEY_ID=''", "AWS_SECRET_ACCESS_KEY=''", "AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"]) {
            sh 'docker login -u AWS -p $(aws ecr-public get-login-password --region us-east-1) public.ecr.aws/h1p2m5p4'
            sh 'docker build -t ecr-demoimg .'
            sh 'docker tag ecr-demoimg:""$BUILD_ID""'
            sh 'docker push docker push public.ecr.aws/h1p2m5p4/ecr-demoimg:""$BUILD_ID""'
            }
          }
        }
      }
    }
        
