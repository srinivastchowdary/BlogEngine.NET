node{
  stage('Upload Artifacts'){
      bat 'curl -uadmin:artifact123 -X PUT ${WORKSPACE}/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip http://192.168.0.203:8081/artifactory/DOTNET-PROJECT/${BUILD_NUMBER}/'
     }
}
