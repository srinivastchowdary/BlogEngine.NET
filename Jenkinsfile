node{
     stage('Upload Artifacts'){
      bat 'curl -uadmin:password -T ${workspace}/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip http://localhost:8081/artifactory/api/storage/DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip'


  }
}
