node{
   stage('SCM Checkout'){
     git 'https://github.com/seenuvasu145/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }  
    stage('Email Notification'){
     mail bcc: '', body: 'Welcome to jenkins notification alert', 
        cc: 'mohamed.sadiqh@gmail.com', from: '', replyTo: '', subject: 'Jenkins job', to: 'vasucena145@gmail.com'
    }
   stage('Slack Notification'){
    slackSend baseUrl: 'https://hooks.slack.com/services/', 
      channel: 'jenkins-pipeline', color: 'good', 
     message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${BUILD_USER}\n More info at: ${env.BUILD_URL}", 
     teamDomain: 'esafe build notification', 
     tokenCredentialId: 'slack-notification'
    }
   stage('Attachment Log'){
   emailext attachLog: true, body: '${currentBuild.result}: ${BUILD_URL}', 
      compressLog: true, replyTo: 'mohamed.sadiqh@gmail.com', 
      subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}', to: 'vasucena145@gmail.com'
   }

}
