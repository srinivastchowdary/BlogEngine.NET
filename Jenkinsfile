node{
     stage('Checkout Code'){
    
        git 'https://github.com/srinivastchowdary/BlogEngine.NET.git'
    }
    stage('Restore Nuget'){
    
        bat 'C:/Users/user/Downloads/nuget.exe restore BlogEngine/BlogEngine.sln'
    }    
 stage('Build'){
       
       bat "\"${tool 'MSBuild'}\" BlogEngine/BlogEngine.sln /t:rebuild /p:VisualStudio=17.0 /p:Configuration=Release /p:DeployOnBuild=True"
        
     }
 stage ('Deploy Artifacts') {

   def server = Artifactory.Server 'Default Artifactory Server'
   def uploadSpec = """{
   "files": [
    {
      "pattern": "(.*).zip",
      "target": "DOTNET-PROJECT/${BUILD_NUMBER}/"
      "recursive": "false"
      "regexp": "true"
    }
  ]
 }"""
 server.upload(uploadSpec)
}
}
