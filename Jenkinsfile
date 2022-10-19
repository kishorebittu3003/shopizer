pipeline {
    agent {label 'GIT_SSH'}
    triggers {
        pollSCM('0 17 * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'developer', url: 'https://github.com/kishorebittu3003/shopizer.git'         
            }
        }
        stage('artifactory') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
            }
        }
        stage('junit'){
            steps{
                junit '**/surefire-reports/*.xml'
            }
        }
    }
}
