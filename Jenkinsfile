  node{
   stage('SCM Checkout'){
     git 'https://github.com/seenuvasu145/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }   
   stage('Slack Notification'){
    slackSend baseUrl: 'https://hooks.slack.com/services/', 
    channel: 'jenkins-pipeline', color: 'good', 
     message: 'welcome to Jenkins slack', 
     teamDomain: 'esafe build notification', 
     tokenCredentialId: 'slack-notification'
    }
    stage('Send attachement file '){
     emailext attachLog: true, body: "${currentBuild.result}: ${BUILD_URL}", 
      compressLog: true, subject: "Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", to: 'vasucena145@gmail.com'
    }
   
}


