node{
   stage('Download Artifacts'){
        
      archiveArtifacts '**/*.zip'
    }
  stage('Upload Artifacts'){
      bat 'curl -uadmin:artifact123 -X PUT ${WORKSPACE}/BlogEngine.NET.zip http://192.168.0.203:8081/artifactory/DOTNET-PROJECT/$BUILD_NUMBER/*.zip'
     }
}
