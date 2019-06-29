node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/my-app.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'MAVEN', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
} 
    stage('Email Notification'){
          mail bcc: '', body: 'Welcome to jenkins notification alert', 
          cc: 'mohamed.sadiqh@gmail.com', from: '', replyTo: '', subject: 'Jenkins job', to: 'vasucena145@gmail.com'

}
     stage('Slack Notification'){
          slackSend baseUrl: 'https://esafeworkspace.slack.com/services/hooks/jenkins-ci/', 
              channel: 'pipeline', color: '"#439FE0", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"', 
              failOnError: true, message: 'Welcome to Jenkin Slack!', 
              teamDomain: 'esafe build notification', token: 'HLIX5MlkTiW9WTeeYMSR14eL', 
              tokenCredentialId: 'jenkins-slack-notification'
}

    stage('Attachment Log'){
          emailext attachLog: true, body: '${currentBuild.result}: ${BUILD_URL}', 
          compressLog: true, replyTo: 'mohamed.sadiqh@gmail.com', 
          subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}', to: 'vasucena145@gmail.com'
}

}
