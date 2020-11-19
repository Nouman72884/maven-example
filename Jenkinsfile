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
                buildName: JOB_NAME,
                buildNumber: BUILD_NUMBER,
                serverId: jenkins-artifactory, // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                spec: '''{
                            "files": [
                                {
                                    "pattern": "pom.xml",
                                    "target": "eurus-docker/pom.xml",
                                    "recursive": "false"
                                }
                                // {
                                //     "pattern": "$WORKSPACE/Digital-Twin-App/frontend/frontend.tar.gz",
                                //     "target": "DigitalTwinWebApp-Frontend/",
                                //     "recursive": "false"
                                // }
                            ]
                    }'''    
                )
        }
    }

        // stage ('Artifactory configuration') {
        //     steps {
        //         rtServer (
        //             id: "jenkins-artifactory",
        //             url: "http://artifactory.eurustechnologies.info/artifactory",
        //         )

        //         rtMavenDeployer (
        //             id: "MAVEN_DEPLOYER",
        //             serverId: "jenkins-artifactory",
        //             releaseRepo: "eurus-docker",
        //             snapshotRepo: "eurus-docker"
        //         )

        //         rtMavenResolver (
        //             id: "MAVEN_RESOLVER",
        //             serverId: "jenkins-artifactory",
        //             releaseRepo: "eurus-docker",
        //             snapshotRepo: "eurus-docker"
        //         )
        //     }
        // }

        // stage ('Exec Maven') {
        //     steps {
        //         rtMavenRun (
        //             tool: MAVEN_TOOL, // Tool name from Jenkins configuration
        //             pom: 'pom.xml',
        //             goals: 'clean install',
        //             deployerId: "MAVEN_DEPLOYER",
        //             resolverId: "MAVEN_RESOLVER"
        //         )
        //     }
        // }

        // stage ('Publish build info') {
        //     steps {
        //         rtPublishBuildInfo (
        //             serverId: "jenkins-artifactory"
        //         )
        //     }
        // }
    }
}