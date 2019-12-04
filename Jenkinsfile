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

    //Artifactory server instance declaration   
   archiveArtifacts artifacts: 'BlogEngine/BlogEngine.NET/obj/Release/Package/*.*', fingerprint: true
   def server = Artifactory.newServer url:'http://localhost:8081/artifactory', username:'admin', password:'password'
   server.setBypassProxy(true)
     
   def uploadSpec = """{
"files": [
    {
   "pattern": "*/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip",
   "target": "DOTNET-PROJECT/",
   "regexp": "false",
   "recursive": "false"
   }
  ]
}"""
    def buildInfo1 = server.upload spec: uploadSpec
	server.publishBuildInfo buildInfo1 
 //server.upload spec: uploadSpec
 //server.upload(uploadSpec)
}
}
