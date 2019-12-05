node{
     stage('Upload Artifacts'){
      bat 'curl -i -uadmin:password -X PUT ${workspace}/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip "http://localhost:8081/artifactory/DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip"'


  }
}
