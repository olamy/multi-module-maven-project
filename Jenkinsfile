pipeline {
  agent any
  stages {
    stage("Build") {
      steps {
        withMaven(
          maven: 'maven-3.9.x'
          mavenOpts:"-Djava.security.manager=com.cloudbees.cbci.fips_security_manager.FIPSSecurityManager -Dorg.bouncycastle.fips.approved_only=true -Xbootclasspath/a:/usr/local/lib/java_fips_ext/bc-fips-1.0.2.3.jar:/usr/local/lib/java_fips_ext/bctls-fips-1.0.12.2.jar:/usr/local/lib/java_fips_ext/bcpkix-fips-1.0.5.jar:/usr/local/lib/java_fips_ext/fips-security-manager-1.0.jar") {
          sh "mvn -V clean verify"
        } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
      }
    }
  }
}
