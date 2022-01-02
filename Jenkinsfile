pipeline {
  agent any
  environment {
    APPSYSID = '411423612fb00110c1dcfcecf699b680'
    BRANCH = "main"
    CREDENTIALS = 'SNOW'
    DEVENV = 'https://devinstance.service-now.com/'
    TESTSUITEID = '632e43900b20220050192f15d6673a7e'
  }
  stages {
    stage('Build') {
      steps {
        snApplyChanges(appSysId: "${APPSYSID}", branchName: "${BRANCH}", url: "${DEVENV}", credentialsId: "${CREDENTIALS}")
        snPublishApp(credentialsId: "${CREDENTIALS}", appSysId: "${APPSYSID}", obtainVersionAutomatically: true, url: "${DEVENV}")
      }
    }
    stage('Test') {
      steps {
        snInstallApp(credentialsId: "${CREDENTIALS}", url: "${DEVENV}", appSysId: "${APPSYSID}")
        snRunTestSuite(credentialsId: "${CREDENTIALS}", url: "${DEVENV}", testSuiteSysId: "${TESTSUITEID}", withResults: true)
      }
    }
    stage('Deploy to Prod') {
      steps {
        echo 'Deployed to PROD'
      }
    }
  }
}
