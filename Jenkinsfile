node{
     
 stage ('Deploy Artifacts') {

   def server = Artifactory.server 'Default Artifactory Server'
      
   def uploadSpec = """{
   "files": [
    {
      "pattern": "BlogEngine.NET.zip",
      "target": "DOTNET-PROJECT/${BUILD_NUMBER}/",
       "props": "type=zip;status=ready",
      "recursive": "false",
      "regexp": "true"
    }
  ]
 }"""
 server.upload(uploadSpec)
}
}
