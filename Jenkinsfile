node{
    
 stage ('Deploy Artifacts') {

    //Artifactory server instance declaration   
    def server = Artifactory.server 'Default Artifactory Server' // Default Artifactory Server is the Server ID given to Artifactory server in Jenkins

   def uploadSpec = """{
"files": [
    {
   "pattern": "${WORKSPACE}/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip",
   "target": "DOTNET-PROJECT/",
   "flat": "true",
   "recursive":"true"
   }
  ]
}"""
 server.upload spec: uploadSpec
}
}
