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
    
    post {  
         always {  
             echo 'This will always run'  
         }  
         success {  
             echo 'This will run only if successful'  
         }  
         failure {  
             mail bcc: '', body: "<b>Example</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "vasucena145@gmail.com";  
         }  
         unstable {  
             echo 'This will run only if the run was marked as unstable'  
         }  
         changed {  
             echo 'This will run only if the state of the Pipeline has changed'  
             echo 'For example, if the Pipeline was previously failing but is now successful'  
         }  
     }  
 }
    stage('Slack Notification'){
    slackSend baseUrl: 'https://hooks.slack.com/services/', 
    channel: 'jenkins-pipeline', color: 'good', 
     message: 'welcome to Jenkins slack', 
     teamDomain: 'esafe build notification', 
     tokenCredentialId: 'slack-notification'
    }
      
    
}


