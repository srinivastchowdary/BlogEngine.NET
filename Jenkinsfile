node{
     stage('Upload Artifacts'){
      bat 'curl -uadmin:password -X PUT ${workspace}/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip http://localhost:8081/artifactory/DOTNET-PROJECT/*.zip'


  }
}
