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
 stage('Upload Artifacts'){
     archiveArtifacts artifacts: '**/*.zip'
     def server = Artifactory.server 'Default Artifactory Server'
     def buildInfo = Artifactory.newBuildInfo()
     buildInfo.env.capture = true
     buildInfo.env.collect()
     server.bypassProxy = true
   
     def uploadSpec = """{
     "files": [
        {
          "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/.*B[A-z]logEngine.*.zip",
          "target": "DOTNET-PROJECT/",
          "regexp": "true"
        },
        {
          "pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/.*(B|b)logEngine.*.zip",
          "target": "DOTNET-PROJECT/",
         "regexp": "true"
        }
    ]
 }"""
  server.upload spec: uploadSpec, buildInfo: buildInfo
 }
}
