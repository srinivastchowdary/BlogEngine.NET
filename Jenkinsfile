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
    stage('Build + SonarQube analysis') {
           bat "\"${tool 'SonarScanner for MSBuild'}/SonarScanner.MSBuild.exe\" begin /k:DOTNET-PROJECT /d:sonar.host.url=http://localhost:9000 /n:DOTNET-PROJECT /v:$BUILD_NUMBER"
           bat "\"${tool 'MSBuild'}\" BlogEngine/BlogEngine.sln /t:Rebuild /p:VisualStudio=17.0 /p:Configuration=Release /p:DeployOnBuild=True"
	          bat "\"${tool 'SonarScanner for MSBuild'}/SonarScanner.MSBuild.exe\" end"
	    
	          def response = httpRequest "http://localhost:9000/api/qualitygates/project_status?projectKey=DOTNET-PROJECT"
        }
 
    stage('Unit Test'){
           bat "del Testresults.trx"
           bat "\"${tool 'MSTest'}\" /testcontainer:BlogEngine/BlogEngine.Tests/bin/Debug/BlogEngine.Tests.dll /resultsfile:Testresults.trx"
       }
     
     stage('Upload Artifacts'){
           archiveArtifacts artifacts: '**/*.zip'
           def server = Artifactory.server 'Default Artifactory Server'
     
           def uploadSpec = """{
           "files": [
            {
              "pattern": "BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip",
               "target": "DOTNET-PROJECT/${BUILD_NUMBER}/"
            }
            ]
            }"""
            server.upload spec: uploadSpec, failNoOp: true
       }
 
  stage('Download Artifacts To Local Machine'){
             def server = Artifactory.server 'Default Artifactory Server'
             def downloadSpec = """{
             "files": [
              {
              "pattern": "DOTNET-PROJECT/$BUILD_NUMBER/*.zip",
              "target": "H:/seenu.net/",
              "flat": "true"
               }
               ]
               }"""
               server.download spec: downloadSpec, failNoOp: true
          }
   stage('Deploy to IIS'){
    
        bat label: '', script: '''"C:\\Program Files\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb=sync -source:package="H:\\seenu.net\\BlogEngine.NET.zip" -dest:auto -setParam:"IIS Web Application Name"="Blogengine" -allowUntrusted=true
    '''
   }
   stage('Attachment Log'){
              emailext attachLog: true, body: '${currentBuild.result}: ${BUILD_URL}', 
              compressLog: true, replyTo: 'mohamed.sadiqh@gmail.com', 
              subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}', to: 'seenuvasu145@gmail.com'
        } 
}
