node{
     stage('Upload Artifacts'){
      bat 'curl  -uadmin:password -X PUT http://localhost:8081/artifactory/api/storage/DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip'
  }
}
