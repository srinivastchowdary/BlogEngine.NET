node{
    
    
  stage('Upload Artifacts'){
       def server = Artifactory.newServer 'Default Artifactory Server'
       server.setBypassProxy(true)
      
	  
       def uploadSpec = """{
       "files": [
       {
          "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
          "target": "DOTNET-PROJECT/BlogEngine.NET.zip"
       }
      ]
    }"""
    server.upload spec: uploadSpec
  }
    
    
}
