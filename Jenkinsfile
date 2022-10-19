pipeline {
    agent {label 'GIT_SSH'}
    triggers {
        pollSCM('0 17 * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/kishorebittu3003/shopizer.git',
                    branch: 'developer'         
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean package'
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
