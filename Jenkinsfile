node {
	stage('Deploy to ansiblesaerver'){
             def server = Artifactory.server 'Default Artifactory Server'
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
       stage('Run Playbook'){
	   
	     sh 'ansible-playbook /opt/ansible/copywarfile.yml'
	}
}
