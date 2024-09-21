pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('continuous integration') {
      steps {
        echo 'hello gourish'
        withMaven() {
          bat 'mvn clean'
          bat(script: 'mvn test cobetura:cobetura install', label: 'code coverage')
          cobertura(autoUpdateHealth: true, autoUpdateStability: true, classCoverageTargets: 'target/site/cobetura/*.xml', coberturaReportFile: 'target/site/cobetura/*.xml', failUnstable: true)
        }

      }
    }

  }
}