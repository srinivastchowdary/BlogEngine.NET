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
    
   stage('Build + SonarQube analysis') {
       
       def sqScannerMsBuildHome = tool 'Scanner for MSBuild'
       withSonarQubeEnv('My SonarQube Server') {
       bat "${sqScannerMsBuildHome}\\SonarQube.Scanner.MSBuild.exe begin /k:DOTNET-PROJECT /d:sonar.host.url=http://localhost:9000 /d:sonar.login=98ee32363c4bb8687315351a054737ea2c480a1f"
       bat 'MSBuild.exe BlogEngine/BlogEngine.sln /t:Rebuild'
       bat "${sqScannerMsBuildHome}\\SonarQube.Scanner.MSBuild.exe end /d:sonar.login=98ee32363c4bb8687315351a054737ea2c480a1f"
    }
  }
    stage('Unit Test'){
     
      bat "\"${tool 'MSTest'}\" /testcontainer:BlogEngine/BlogEngine.Tests/bin/Debug/BlogEngine.Tests.dll"
    }
    
    stage('Download Artifacts'){
        
      archiveArtifacts '**/*.zip'
    }
    
    stage('Deploy to IIS'){
    
        "C:/Program Files/IIS/Microsoft Web Deploy V3/msdeploy.exe -verb=sync -source:package=C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip -dest:auto -setParam:IIS Web Application Name=BlogEngine -allowUntrusted=true"
    }
    
    stage('Attachment Log'){
                 emailext attachLog: true, body: '${currentBuild.result}: ${BUILD_URL}', 
                 compressLog: true, replyTo: 'mohamed.sadiqh@gmail.com', 
                 subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}', to: 'seenuvasu145@gmail.com'
            } 
}
