  node{
   stage('SCM Checkout'){
     git 'https://github.com/seenuvasu145/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
    stage('Build'){
            steps {
                echo "Running job: ${env.JOB_NAME}\nbuild: ${env.BUILD_ID} - ${env.BUILD_URL}\nblue ocean: ${env.RUN_DISPLAY_URL}"
            }
        }
    }
    post {
        failure {
            mail to: 'senuvasu145@gmail.com', from: 'vasucena@145.com',
                subject: "Example Build: ${env.JOB_NAME} - Failed", 
                body: "Job Failed - \"${env.JOB_NAME}\" build: ${env.BUILD_NUMBER}\n\nView the log at:\n ${env.BUILD_URL}\n\nBlue Ocean:\n${env.RUN_DISPLAY_URL}"
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
    
}


