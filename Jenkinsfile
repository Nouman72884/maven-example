pipeline {
    environment {
        BUILD_NUM = ''

    }
    agent any
    stages {
        stage('Build Job1') {
            steps {
              script {

                  def  build_job: "001_job" 
                   def build_num1 = build_job.getNumber()
                 BUILD_NUM = "${build_num1}"
                 echo BUILD_NUM  //build number of oo1/job
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