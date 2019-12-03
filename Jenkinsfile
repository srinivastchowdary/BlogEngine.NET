node{
    
 stage('Upload Artifacts'){
  withCredentials([usernameColonPassword(credentialsId: 'Aartifactory-Account', variable: 'Artifactory-credentials')]) {
  bat curl -u${Artifactory-credentials} -T C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/BlogEngine.NET.zip "http://localhost:8081/artifactory/DOTNET-PROJECT/BlogEngine.NET.zip"  
}
}
