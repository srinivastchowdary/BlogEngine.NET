node{
     stage('Upload Artifacts'){
      bat 'curl -uadmin:password -X PUT C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip http://192.168.0.203:8081/artifactory/api/storage/Esafe-Project/${BUILD_NUMBER}/BlogEngine.NET.zip'


  }
}
