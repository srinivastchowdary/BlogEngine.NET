node{
  
stage ('Publish'){
         archiveArtifacts artifacts: '**/*.zip', fingerprint: true
	 def server = Artifactory.newServer url:'http://192.168.0.203:8081/artifactory', username:'admin', password:'artifact123'
    	 //def server = Artifactory.server 'Artifactory Server'
         server.setBypassProxy(true)

    		def uploadSpec = """{
    		"files": [
    		{
     		"pattern": ".Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
     		"target": "DOTNET-PROJECT/${BUILD_NUMBER}/"
   		}
        	]
		}"""
		def buildInfo1 = server.upload spec: uploadSpec
	        server.publishBuildInfo buildInfo1 
	}

}
