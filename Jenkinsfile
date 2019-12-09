node{
 stage('Checkout Code'){
    
        git 'https://github.com/srinivastchowdary/BlogEngine.NET.git'
    }
    stage('Restore Nuget'){
    
        bat 'C:/Users/user/Downloads/nuget.exe restore BlogEngine/BlogEngine.sln'
    }    
 stage('Upload Artifacts'){
     archiveArtifacts artifacts: '**/*.zip'
     def server = Artifactory.server 'Default Artifactory Server'
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
