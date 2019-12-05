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
      bat 'curl -i -uadmin:password -X PUT ${WORKSPACE}/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip http://localhost:8081/artifactory/api/storage/DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip'
     }
}
