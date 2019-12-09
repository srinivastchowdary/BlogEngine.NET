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
      bat label: '', script: '''curl -uadmin:password -T "C:\\Program Files (x86)\\Jenkins\\workspace\\.Net-Project_Pipeline\\BlogEngine\\BlogEngine.NET\\obj\\Release\\Package\\BlogEngine.NET.zip" "http://localhost:8081/artifactory/DOTNET-PROJECT/BlogEngine.NET.zip --build-name=my-build-name --build-number=18

"
'''
  }
}
