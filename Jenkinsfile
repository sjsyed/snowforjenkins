pipeline {
  agent any
  environment {
    APPSYSID = '411423612fb00110c1dcfcecf699b680'
    BRANCH = "main"
    CREDENTIALS = 'ServiceNow'
    DEVENV = 'https://dev75674.service-now.com/'
    TESTSUITEID = '632e43900b20220050192f15d6673a7e'
  }
  stages {
    stage('Build') {
      steps {
        echo "${CREDENTIALS}"
        snApplyChanges(appSysId: "${APPSYSID}", branchName: "${BRANCH}", url: "${DEVENV}", credentialsId: "${CREDENTIALS}")
      }
    }
    stage('Test') {
      steps {
        snRunTestSuite(browserName: 'Firefox', osName: 'Windows', osVersion: '10', testSuiteSysId: "${TESTSUITEID}", withResults: true)
      }
    }
    stage('Deploy to Prod') {
      steps {
        echo 'Deployed to PROD'
      }
    }
  }
}
