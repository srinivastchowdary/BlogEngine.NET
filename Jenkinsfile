node{
    
    stage('Checkout Code'){
    
        git 'https://github.com/srinivastchowdary/BlogEngine.NET.git'
    }
    stage('Restore Nuget'){
    
        bat 'C:/Users/user/Downloads/nuget.exe restore BlogEngine/BlogEngine.sln'
    }    
 // stage('Build'){
       
   //    bat "\"${tool 'MSBuild'}\" BlogEngine/BlogEngine.sln /t:rebuild /p:VisualStudio=17.0 /p:Configuration=Release /p:DeployOnBuild=True"
        
     //}
 //   stage('Build + SonarQube analysis') {
   //           bat "\"${tool 'SonarScanner for MSBuild'}/SonarScanner.MSBuild.exe\" begin /k:DOTNET-PROJECT /d:sonar.host.url=http://localhost:9000 /n:DOTNET-PROJECT /v:$BUILD_NUMBER"
     //         bat "\"${tool 'MSBuild'}\" BlogEngine/BlogEngine.sln /t:Rebuild /p:VisualStudio=17.0 /p:Configuration=Release /p:DeployOnBuild=True"
	//          bat "\"${tool 'SonarScanner for MSBuild'}/SonarScanner.MSBuild.exe\" end"
	    
	  //  def response = httpRequest "http://localhost:9000/api/qualitygates/project_status?projectKey=DOTNET-PROJECT"


  //}
 
    stage('Unit Test'){
     
      bat "\"${tool 'MSTest'}\" /testcontainer:BlogEngine/BlogEngine.Tests/bin/Debug/BlogEngine.Tests.dll"
    }
    
    stage('Download Artifacts'){
        
      archiveArtifacts '**/*.zip'
    }
  stage('Upload Artifacts'){
      bat label: '', script: '''curl -uadmin:password -T "C:\\Program Files (x86)\\Jenkins\\workspace\\.Net-Project_Pipeline\\BlogEngine\\BlogEngine.NET\\obj\\Release\\Package\\BlogEngine.NET.zip" "http://localhost:8081/artifactory/DOTNET-PROJECT/${buildName}/BlogEngine.NET.zip?properties=build.number"
'''
  }
	
 stage('Download Artifacts'){
	
	 bat label: '', script: 'curl -H \'X-JFrog-Art-Api:AP9f8B2sPwKyBspLxTzC9TeN9Q\' -O "http://localhost:8081/artifactory/DOTNET-PROJECT/BlogEngine.NET.zip" "H:\\seenu.net\\BlogEngine.NET.zip"'
	}
    
 //   stage('Deploy to IIS'){
    
  // bat label: '', script: '''"C:\\Program Files\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb=sync -source:package="C:\\Program Files (x86)\\Jenkins\\workspace\\.Net-Project\\BlogEngine\\BlogEngine.NET\\obj\\Release\\_PublishedWebsites\\BlogEngine.NET_Package\\BlogEngine.NET.zip" -dest:auto -setParam:"IIS Web Application Name"="dotnetproject" -allowUntrusted=true
//'''
  //  }
    
    //stage('Attachment Log'){
      //           emailext attachLog: true, body: '${currentBuild.result}: ${BUILD_URL}', 
        //         compressLog: true, replyTo: 'mohamed.sadiqh@gmail.com', 
          //       subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}', to: 'seenuvasu145@gmail.com'
           //} 
}
