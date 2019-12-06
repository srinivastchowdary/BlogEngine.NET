node{
 stage ('Publish'){
                archiveArtifacts '**/*.zip'
    		        def server = Artifactory.server 'Artifactory Server'
                def uploadSpec = """{
                 "files": [
                  {
                   "pattern": "(.*).zip",
                   "target": "DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip"
                   "recursive": "false"
                   "regexp": "true"
                  }
                  ]
               }"""
            server.upload(uploadSpec)
   }
}
