node{
 stage('Checkout Code'){
    
        git 'https://github.com/srinivastchowdary/BlogEngine.NET.git'
    }
    stage('Restore Nuget'){
    
        bat 'C:/Users/user/Downloads/nuget.exe restore BlogEngine/BlogEngine.sln'
    } 
 // stage('Build'){
       
 //      bat "\"${tool 'MSBuild'}\" BlogEngine/BlogEngine.sln /t:rebuild /p:VisualStudio=17.0 /p:Configuration=Release /p:DeployOnBuild=True"
        
   //  }
stage('Upload Artifacts'){
     archiveArtifacts artifacts: '**/*.zip'
     def server = Artifactory.server 'Default Artifactory Server'
     //def buildInfo = Artifactory.newBuildInfo()
 
      def buildInfo = server.upload(uploadSpec)
      buildInfo.env.capture = true
     
     

    def uploadSpec = """{
     "files": [
      {
       "pattern": "Package/*BlogEngine*.zip",
       "target": "DOTNET-PROJECT/"
      }
     ]
    }"""
   server.upload(uploadSpec)
   server.publishBuildInfo(buildInfo)
   //server.upload(artifactoryUploadDsl, buildInfo)
  // server.publishBuildInfo(buildInfo)
  
  }
}
