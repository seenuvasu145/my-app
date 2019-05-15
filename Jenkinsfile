node{
   stage('SCM Checkout'){
     git 'https://github.com/seenuvasu145/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }   
   post {
        failure {
            script {
                mail (to: 'vasucena145@gmail.com',
                        subject: "Job '${env.JOB_NAME}' (${env.BUILD_NUMBER}) failed",
                        body: "Please visit ${env.BUILD_URL} for further information"
                );
                }
            }
         success {
             script {
                mail (to: 'vasucena145@gmail.com',
                        subject: "Job '${env.JOB_NAME}' (${env.BUILD_NUMBER}) success.",
                        body: "Please visit ${env.BUILD_URL} for further information.",


                  );
                }
          }      
    }
   
}
