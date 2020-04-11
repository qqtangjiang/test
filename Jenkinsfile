pipeline {
  agent any
  stages {
    stage('检出') {
      steps {
        checkout([
          $class: 'GitSCM', branches: [[name: env.GIT_BUILD_REF]],
          userRemoteConfigs: [[
            url: env.GIT_REPO_URL,
            credentialsId: env.CREDENTIALS_ID
          ]]
        ])
        sh '''set
echo $GIT_BUILD_REF
curl "$JENKINS_URL"credentials/store/system/domain/_/api/json?pretty=true'''
      }
    }
  }
}