node{
    
    stage('Checkout Code'){
    
        git 'https://github.com/srinivastchowdary/BlogEngine.NET.git'
    }
    stage('Restore Nuget'){
    
        bat 'C:/Users/user/Downloads/nuget.exe restore BlogEngine/BlogEngine.sln'
    }    
   stage('Build'){
       
       bat "\"${tool 'MSBuild'}\" BlogEngine/BlogEngine.sln /t:clean;build;package 
       /p:PackageFileName="C:\Program Files (x86)\Jenkins\workspace\.Net-Project_Pipeline\BlogEngine\BlogEngine.NET\obj\Debug\Package\BlogEngine.NET.zip""
        
     }
    stage('Unit Test'){
     
      bat "\"${tool 'MSTest'}\" /testcontainer:BlogEngine/BlogEngine.Tests/bin/Debug/BlogEngine.Tests.dll"
    }
    
    stage('Create Artifacts'){
        
      archiveArtifacts '**/*.zip'
    }
}
