pipeline {
  agent any
  environment {
    APPSYSID = '411423612fb00110c1dcfcecf699b680'
    BRANCH = "main"
    CREDENTIALS = 'ServiceNow'
    DEVENV = 'https://dev75674.service-now.com/'
    TESTSUITEID = '17a099962f300110c1dcfcecf699b621'
  }
  stages {
    stage('Build') {
      steps {
        echo "${CREDENTIALS}"
        snApplyChanges(appSysId: "${APPSYSID}", branchName: "${BRANCH}", url: "${DEVENV}", credentialsId: "${CREDENTIALS}")
        //snPublishApp(credentialsId: "${CREDENTIALS}", appSysId: "${APPSYSID}", obtainVersionAutomatically: true, url: "${DEVENV}")
      }
    }
    stage('Test') {
      steps {
        //snInstallApp(credentialsId: "${CREDENTIALS}", url: "${DEVENV}", appSysId: "${APPSYSID}")
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
