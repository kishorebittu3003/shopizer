pipeline {
    agent {label 'GIT_SSH'}
    triggers {
        pollSCM('0 17 * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'git@github.com:kishorebittu3003/shopizer.git',
                    branch: 'master',       
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}