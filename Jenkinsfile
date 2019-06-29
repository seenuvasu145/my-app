node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/my-app.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'MAVEN', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
} 
     stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'MAVEN', type: 'maven'
        withSonarQubeEnv('Default SonarQube Server') { 
          sh "${mvnHome}/bin/mvn sonar:sonar"
        }
}
    stage('Email Notification'){
          mail bcc: '', body: 'Welcome to jenkins notification alert', 
          cc: 'mohamed.sadiqh@gmail.com', from: '', replyTo: '', subject: 'Jenkins job', to: 'vasucena145@gmail.com'

}
     stage('Slack Notification'){
           slackSend baseUrl: 'https://esafeworkspace.slack.com/services/hooks/jenkins-ci/', 
           channel: '#pipeline', color: 'good', 
           message:"${currentBuild.result}: ${BUILD_URL} ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", 
           teamDomain: 'esafe build notification', 
           tokenCredentialId: 'jenkins-slack-notification',
           body: '${currentBuild.result}: ${BUILD_URL}',
           subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}'

}

    stage('Attachment Log'){
          emailext attachLog: true, body: '${currentBuild.result}: ${BUILD_URL}', 
          compressLog: true, replyTo: 'mohamed.sadiqh@gmail.com', 
          subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}', to: 'vasucena145@gmail.com'
}

}
