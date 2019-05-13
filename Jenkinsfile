  node{
   stage('SCM Checkout'){
     git 'https://github.com/seenuvasu145/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
    stage('Email Notification'){
       mail bcc: '', body: '''Hi welcome to jenkins email alerts
       Thanks
       seenu''', cc: 'mohamed.sadiqh@gmail.com', from: '', replyTo: '', subject: 'Jenkins Job', to: 'vasucena145@gmail.com'
    }
    stage('Slack Notification'){
    slackSend baseUrl: 'https://hooks.slack.com/services/', 
    channel: 'jenkins-pipeline', color: 'good', 
     message: 'welcome to Jenkins slack', 
     teamDomain: 'esafe build notification', 
     tokenCredentialId: 'slack-notification'
    }
       stage('Download') {
            steps {
                sh 'echo "artifact file" > generatedFile.txt'
            }
        }
    
    post {
        always {
            archiveArtifacts artifacts: 'generatedFile.txt', onlyIfSuccessful: true
            
            echo 'I will always say Hello again!'
                
            emailext attachLog: true, attachmentsPattern: 'generatedFile.txt',
                body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
                recipientProviders: [developers(), requestor()],
                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
            
        }
    }
}


