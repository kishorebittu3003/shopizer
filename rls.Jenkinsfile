pipeline {
    agent any
    triggers{
        pollSCM('30 17 * * *')
    }
    stages {
        stage ('Clone') {
            steps {
                git url: 'https://github.com/kishorebittu3003/shopizer.git',
                    branch: 'realease'
            }
        }

        stage ('Artifactory configuration') {
            steps {
                rtMavenDeployer (
                    id: "JFROG_JENKINS",
                    serverId:  "JFROG_JENKINS",
                    releaseRepo: 'rajee-libs-release-local',
                    snapshotRepo: 'rajee-libs-snapshot-local'
                )
            }
        }

        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    tool: 'MAVEN_3.6.3', // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "JFROG_JENKINS"
                    
                )

            }

        stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "JFROG_JENKINS"
                )
            }
        }
    }
}
}