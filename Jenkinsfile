node{
 stage ('Publish'){
             bat label: '', script: '''curl -X PUT -u admin:artifact123 -T **/*.zip "http://192.168.0.203:8081/artifactory/DOTNET-PROJECT/${BUILD_NUMBER}/BlogEngine.NET.zip"
'''
   }
}
