node{
    
    
  stage('Upload Artifacts'){
       def server = Artifactory.newServer url: 'http://localhost:8081/artifactory', username: 'admin', password: 'password'
       server.setBypassProxy(true)
      
	  
       def uploadSpec = """{
       "files": [
       {
          "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
          "target": "DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip"
       }
      ]
    }"""
    server.upload spec: uploadSpec
  }
    
    
}
