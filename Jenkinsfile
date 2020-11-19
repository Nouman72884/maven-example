pipeline {
    agent any
    stages {
        stage ('Clone') {
            steps {
                git url: "https://github.com/Nouman72884/maven-example.git"
            }
        }

        stage ('Artifactory configuration') {
            steps {
                rtServer (
                    id: "jenkins-artifactory",
                    url: "http://artifactory.eurustechnologies.info/artifactory",
                    credentialsId: CREDENTIALS
                )

                rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId: "jenkins-artifactory",
                    releaseRepo: "eurus-docker",
                    snapshotRepo: "eurus-docker"
                )

                rtMavenResolver (
                    id: "MAVEN_RESOLVER",
                    serverId: "jenkins-artifactory",
                    releaseRepo: "eurus-docker",
                    snapshotRepo: "eurus-docker"
                )
            }
        }

        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    tool: MAVEN_TOOL, // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "MAVEN_DEPLOYER",
                    resolverId: "MAVEN_RESOLVER"
                )
            }
        }

        stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "jenkins-artifactory"
                )
            }
        }
    }
}