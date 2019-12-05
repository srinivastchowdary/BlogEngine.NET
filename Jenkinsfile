node{
     stage('Upload Artifacts'){
      bat 'curl -H -uadmin:password -X PUT "http://http://localhost:8081/artifactory/api/storage/DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip'
  }
}
