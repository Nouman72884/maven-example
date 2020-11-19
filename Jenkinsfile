pipeline {
    agent any
    stages {
        stage ('Clone') {
            steps {
                git url: "https://github.com/Nouman72884/maven-example.git"
            }
        }

        stage ('Publish Artifacts') {
        steps {
            rtUpload (
                serverId: "jenkins-artifactory", // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                spec: """{
                            "files": [
                                {
                                    "pattern": "pom.xml",
                                    "target": "pom.xml",
                                    "recursive": "false"
                                }
                            ]
                    }"""   
                )
        }
    }

    
    }
}