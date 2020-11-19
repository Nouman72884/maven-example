pipeline {
    environment {
        BUILD_NUM = ''

    }
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
                buildName: JOB_NAME,
                buildNumber: BUILD_NUMBER,
                serverId: "jenkins-artifactory", // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                spec: """{
                            "files": [
                                {
                                    "pattern": "pom.xml",
                                    "target": "wajahat/pom.xml",
                                    "recursive": "false"
                                }
                            ]
                    }"""   
                )
        }
    }
        // stage ('Publish build info') {
        //     steps {
        //         rtPublishBuildInfo (
        //             serverId: "jenkins-artifactory"
        //         )
        //     }
        // }
    }
}