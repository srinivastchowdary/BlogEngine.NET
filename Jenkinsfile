node{
 stage ('Publish'){
                archiveArtifacts '**/*.zip'
    		        def server = Artifactory.server 'Artifactory Server'
                def uploadSpec = """{
                 "files": [
                  {
                   "pattern": "**/BlogEngine.NET.zip",
                   "target": "DOTNET-PROJECT/.$BUILD_NUMBER.zip",
                   "recursive": "false",
                   "regexp": "true"
                  }
                  ]
               }"""
            server.upload(uploadSpec)
   }
}
