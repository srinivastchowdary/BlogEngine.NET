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
stage('Unit Test'){
     
      bat "\"${tool 'MSTest'}\" /testcontainer:BlogEngine/BlogEngine.Tests/bin/Debug/BlogEngine.Tests.dll /del:Testresults.trx /resultsfile:Testresults.trx"
    }
}
