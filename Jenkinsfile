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
        
     bat 'C:/Program Files (x86)/Microsoft Visual Studio/2017/Community/Common7/IDE/MSTest.exe' ${workspace}/bin/Debug/BlogEngine.Tests.dll /resultsfile:TestResults.trx


    }
}
