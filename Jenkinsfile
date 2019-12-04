node{
   def serverArtifactory = Artifactory.server 'Default Artifactory Server'
   def uploadSpec = """{
      "files": [
        {
          "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
          "target": "DOTNET-PROJECT/${BUILD_NUMBER}/"
        }
     ]
    }"""
serverArtifactory.upload(uploadSpec)  
}
