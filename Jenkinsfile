node{
    
    stage('Checkout Code'){
    
        git 'https://github.com/srinivastchowdary/BlogEngine.NET.git'
    }
    stage('Restore Nuget'){
    
        bat 'C:/Users/user/Downloads/nuget.exe restore BlogEngine/BlogEngine.sln'
    }    
   stage('Build'){
       
       bat "\"${tool 'MSBuild'}\" BlogEngine/BlogEngine.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
        
     }
    stage('Unit Test'){
      bat "\"${tool 'MSTest'}\" /testcontainer:BlogEngine/BlogEngine.Tests/bin/Debug/BlogEngine.Tests.dll /resultsfile:testResults.trx"
    }
    
    stage('Deploy to IIS'){
      
        bat "C:\Program Files\IIS\Microsoft Web Deploy V3\msdeploy.exe" -verb=sync -source:package="C:\Program Files (x86)\Jenkins\workspace\.Net-Project\BlogEngine\BlogEngine.NET\obj\Release\_PublishedWebsites\BlogEngine.NET_Package\BlogEngine.NET.zip" -dest:auto -setParam:"IIS Web Application Name"="BlogEngine" -allowUntrusted=true
    }
}
