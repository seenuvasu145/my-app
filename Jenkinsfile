node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/my-app.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'maven-3', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
} 
    stage ('Publish'){
    		def server = Artifactory.server 'Default Artifactory Server(centos)'
    		def uploadSpec = """{
    		"files": [
    		{
     		"pattern": "target/myweb-0.0.5.war",
     		"target": "Esafe-Project/${BUILD_NUMBER}/",
	 	"props": "Integration-Tested=Yes;Performance-Tested=No"
   		}
           	]
		}"""
		server.upload(uploadSpec)
	}
	 stash includes: 'target/myweb-0.0.5.war,src/pt/Hello_World_Test_Plan.jmx', name: 'binary'

     stage ('Copy warfile to Ansibleserver'){
           def server = Artifactory.server 'Default Artifactory Server(centos)'
           def downloadSpec = """{
           "files": [
           {
           "pattern": "Esafe-Project/$BUILD_NUMBER/*.war",
           "target": "/opt/ansible/",
           "props": "Performance-Tested=Yes;Integration-Tested=Yes",
           "flat": "true"
           }
           ]
           }"""
           server.download(downloadSpec)
    }
}
