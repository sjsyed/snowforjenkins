pipeline {
  agent any
  environment {
    APPSYSID = '411423612fb00110c1dcfcecf699b680'
    BRANCH = "main"
    CREDENTIALS = 'ServiceNow'
    DEVENV = 'https://dev75674.service-now.com/'
    TESTSUITEID = 'c70c14ca2fbc0110c1dcfcecf699b6c0'
  }
  stages {
//     stage('Build') {
//       steps {
//         echo "${CREDENTIALS}"
//         snApplyChanges(appSysId: "${APPSYSID}", branchName: "${BRANCH}", url: "${DEVENV}", credentialsId: "${CREDENTIALS}")
//         //snPublishApp(credentialsId: "${CREDENTIALS}", appSysId: "${APPSYSID}", obtainVersionAutomatically: true, url: "${DEVENV}")
//       }
//     }
    stage('Test') {
      steps {
        //snInstallApp(credentialsId: "${CREDENTIALS}", url: "${DEVENV}", appSysId: "${APPSYSID}")
        snRunTestSuite(credentialsId: "${CREDENTIALS}", url: "${DEVENV}", testSuiteSysId: "${TESTSUITEID}", withResults: true) 
//         snRunTestSuite(credentialsId: "${CREDENTIALS}", url: "${DEVENV}", testSuiteName: "Simple Parent Test Suite", withResults: true)
      }
    }
    stage('Deploy to Prod') {
      steps {
        echo 'Deployed to PROD'
      }
    }
  }
}
