node{
    
stage ('Deploy Artifacts') {

    //Artifactory server instance declaration   
    def server = Artifactory.server 'Default Artifactory Server' // Default Artifactory Server is the Server ID given to Artifactory server in Jenkins

    //Capturing the Build artifacts from Build server to upload
    def uploadSpec = """{
        "files": [
            {
                "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip",
                "target": "DOTNET-PROJECT/"
            }
        ]
    }"""
    server.upload(uploadSpec)    
  }
}
