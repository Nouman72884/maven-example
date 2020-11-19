pipeline {
    agent any
    stages {
        stage('Build Job1') {
            steps {
              script {

                   build job: "001_job" 
                   $build_001= env.BUILD_NUMBER of 001_job                  
                   echo env.BUILD_NUMBER //this echos the build number of this job and not 001_job
            }
            } 
        } 
        stage ('Clone') {
            steps {
                git url: "https://github.com/Nouman72884/maven-example.git"
            }
        }

    //     stage ('Publish Artifacts') {
    //     steps {
    //         rtUpload (
    //             buildName: JOB_NAME,
    //             buildNumber: BUILD_NUMBER,
    //             serverId: "jenkins-artifactory", // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
    //             spec: """{
    //                         "files": [
    //                             {
    //                                 "pattern": "pom.xml",
    //                                 "target": "wajahat/pom.xml",
    //                                 "recursive": "false"
    //                             }
    //                         ]
    //                 }"""   
    //             )
    //     }
    // }

    
    }
}