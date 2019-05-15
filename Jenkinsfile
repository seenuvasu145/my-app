node{
   stage('SCM Checkout'){
     git 'https://github.com/seenuvasu145/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }  
    stage('Email Notification'){
     mail bcc: '', body: '''Welcome to jenkins job alert
     Thanks
     seenu''', cc: 'mohamed.sadiqh@gmail.com', from: '', replyTo: '', subject: 'Jenkins job', to: 'vasucena145@gmail.com'
    }
   
}
