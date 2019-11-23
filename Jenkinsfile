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
    stage('Test'){
        
      bat "\"${tool 'MStest'}\" C:\Program Files (x86)\Jenkins\workspace\.Net-Project\BlogEngine\BlogEngine.Tests\bin\Debug\BlogEngine.Tests.dll"
    }
}
