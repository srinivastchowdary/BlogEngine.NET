node{
   
  stage('Upload Artifacts'){
      bat 'curl -uadmin:artifact123 -X PUT ${WORKSPACE}/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip http://192.168.0.203:8081/artifactory/api/storage/DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip'
     }
}
