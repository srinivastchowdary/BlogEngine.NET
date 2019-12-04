node{
    
 stage ('Deploy Artifacts') {

    //Artifactory server instance declaration   
   archiveArtifacts artifacts: 'BlogEngine/BlogEngine.NET/obj/Release/Package/*.*', fingerprint: true
   def server = Artifactory.newServer url:'http://localhost:8081/artifactory', username:'admin', password:'password'
   server.setBypassProxy(true)
     
   def uploadSpec = """{
"files": [
    {
   "pattern": "*/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip",
   "target": "DOTNET-PROJECT/",
   "regexp": "false",
   "recursive": "false"
   }
  ]
}"""
 //server.upload spec: uploadSpec
 server.upload(uploadSpec)
}
}
