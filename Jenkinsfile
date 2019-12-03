node{
    
    
  stage('Upload Artifacts'){
       def server = Artifactory.newServer 'Default Artifactory Server'
     
       def uploadSpec = """{
       "files": [
       {
          "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
          "target": "DOTNET-PROJECT/${BUILD_NUMBER}/"
       }
      ]
    }"""
    def buildInfo1 = server.upload spec: uploadSpec
	server.publishBuildInfo buildInfo1 
  }
    
    
}
