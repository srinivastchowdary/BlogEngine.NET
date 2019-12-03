node{
    
 stage('Upload Artifacts'){
       def server = Artifactory.server url: 'http://localhost:8081/artifactory', credentialsId: 'Aartifactory-Account-credentials'
     
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
