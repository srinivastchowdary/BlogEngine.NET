node{
  
stage ('Publish'){
         archiveArtifacts artifacts: '**/*.zip'
    	 def server = Artifactory.server 'Artifactory Server'
         server.setBypassProxy(true)

    		def uploadSpec = """{
    		"files": [
    		{
     		"pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
     		"target": "DOTNET-PROJECT/${BUILD_NUMBER}/"
   		}
        	]
		}"""
		server.upload(uploadSpec)
	}

}
