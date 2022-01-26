@Library(['ciinabox-unique-tags']) _

pipeline {
  environment {
    OPS_ACCOUNT_ID = 537712071186
    AWS_REGION     = 'us-east-1'
    PROJECT_NAME   = 'test-docker-tags'
    ECR_REPO       = "${env.OPS_ACCOUNT_ID}.dkr.ecr.${env.AWS_REGION}.amazonaws.com"
  }

  stages {
    agent {
      label 'docker'
    }

    stage('Test') {
      steps {
        ecr accountId: env.OPS_ACCOUNT_ID,
          region: env.AWS_REGION,
          image: env.PROJECT_NAME

        dockerBuild repo: env.ECR_REPO,
          image: env.PROJECT_NAME,
          tags: ['test',  'test'],
          push: true,
          cleanup: true
      }
    }

  }
}