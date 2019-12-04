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
   "pattern": ".Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
   "target": "DOTNET-PROJECT/",
   "regexp": "true",
   "recursive": "false"
   }
  ]
}"""
 server.upload(uploadSpec)
}
}
