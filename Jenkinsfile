node {
   //def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/Vyacheslav-Lapin/spring-petclinic.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.
      //mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
      //withEnv(["MVN_HOME=$mvnHome"]) {
         //if (isUnix()) {
            sh './mvnw -Dmaven.test.failure.ignore verify'
         //} else {
         //   bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean package/)
         //}
      //}
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
      try {
        emailext body: 'body of email', subject: 'kjhdfkjhdfg', to: 'Vyacheslav.Lapin@gmail.com'
      } catch (Throwable e) {
        echo "Не удалось послать письмо!.."
      }
   }
}
