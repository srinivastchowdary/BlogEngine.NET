node{
     
 stage ('Deploy Artifacts') {

   def server = Artifactory.server 'Default Artifactory Server'
      
   def uploadSpec = """{
   "files": [
    {
      "pattern": "(.*).zip",
      "target": "DOTNET-PROJECT/${BUILD_NUMBER}/",
      "recursive": "false",
      "regexp": "true"
    }
  ]
 }"""
 server.upload(uploadSpec)
}
}
