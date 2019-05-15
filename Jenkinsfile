node{
   stage('SCM Checkout'){
     git 'https://github.com/seenuvasu145/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }  
    stage('Email Notification'){
     emailext attachLog: true, body: '${currentBuild.result}: ${BUILD_URL}', 
        compressLog: true, replyTo: 'mohamed.sadiqh@gmail.com', 
        subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}', to: 'vasucena145@gmail.com'
    }
}
