pipeline {
  agent any
  stages {
    stage("Build") {
      steps {
        withMaven(
          maven: 'maven-3.9.x'
          mavenOpts:"-Xbootclasspath/a:/usr/share/jenkins/fips/bc-fips.jar:/usr/share/jenkins/fips/bctls-fips.jar:/usr/share/jenkins/fips/bcpkix-fips.jar:/usr/share/jenkins/fips/fips-security-manager.jar -Dorg.bouncycastle.fips.approved_only=true -Djava.security.manager=com.cloudbees.cbci.fips_security_manager.FIPSSecurityManager -Djavax.net.ssl.trustStoreType=PKCS12 -Djenkins.security.FIPS140.COMPLIANCE=true -Dcom.redhat.fips=false") {
          sh "mvn -V clean verify"
        } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
      }
    }
  }
}
