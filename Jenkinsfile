node{
   stage('SCM Checkout'){
     git 'https://github.com/seenuvasu145/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }  
    stage('Email Notification'){
     mail bcc: '', body: "${currentBuild.result}: ${BUILD_URL}"
     Thanks
     seenu''', cc: 'mohamed.sadiqh@gmail.com', from: '', 
     replyTo: '', ""Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", to: 'vasucena145@gmail.com'
    }
   
}
