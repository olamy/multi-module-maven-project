pipeline {
  agent any
  stages {
    stage("Build") {
      steps {
        withMaven(maven: 'maven-3.9.x') {
          sh "mvn -V clean verify"
        } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
      }
    }
  }
}
