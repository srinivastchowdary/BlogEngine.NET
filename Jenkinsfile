node{
    
 stage ('Deploy Artifacts') {

    //Artifactory server instance declaration   
   def server = Artifactory.newServer url:'http://localhost:8081/artifactory', username:'admin', password:'password'
   server.setBypassProxy(true)
     
   def uploadSpec = """{
"files": [
    {
   "pattern": "${WORKSPACE}/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip",
   "target": "DOTNET-PROJECT",
   "flat": "true",
   "recursive":"true"
   }
  ]
}"""
 server.upload spec: uploadSpec
}
}
