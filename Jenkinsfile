node{
    
 stage ('Deploy Artifacts') {

    //Artifactory server instance declaration   
    def server = Artifactory.server 'Default Artifactory Server' // Default Artifactory Server is the Server ID given to Artifactory server in Jenkins

   def uploadSpec = """{
"files": [
    {
      "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*BlogEngine.NET*.zip",
      "target": "DOTNET-PROJECT/",
      "props": "p1=v1;p2=v2"
    },
    {
      "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
      "target": "DOTNET-PROJECT/"
    }
  ]
}"""
 server.upload spec: uploadSpec
}
}
