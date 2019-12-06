node{
 stage ('Publish'){
    		def server = Artifactory.server 'Artifactory Server'
    		def uploadSpec = """{
    		"files": [
    		{
     		"pattern": "C:/Program Files (x86)/Jenkins/workspace/.Net-Project_Pipeline/BlogEngine/BlogEngine.NET/obj/Release/Package/*.zip",
     		"target": "DOTNET-PROJECT/${BUILD_NUMBER}/"
   		}
           	]
		}"""
		server.upload(uploadSpec)
	}
}
