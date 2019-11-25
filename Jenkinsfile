node{
    
    stage('Checkout Code'){
    
        git 'https://github.com/srinivastchowdary/BlogEngine.NET.git'
    }
    stage('Restore Nuget'){
    
        bat 'C:/Users/user/Downloads/nuget.exe restore BlogEngine/BlogEngine.sln'
    }    
   stage('Build'){
       
       bat "\"${tool 'MSBuild'}\" BlogEngine/BlogEngine.sln"
        
     }
    stage('Unit Test'){
     
      bat "\"${tool 'MSTest'}\" /testcontainer:BlogEngine/BlogEngine.Tests/bin/Debug/BlogEngine.Tests.dll"
    }
    
    stage('Create Artifacts'){
        
      archiveArtifacts '**/*.zip'
    }
}
