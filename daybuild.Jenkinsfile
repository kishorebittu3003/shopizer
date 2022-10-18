pipeline{
    agent {label 'JVM'}
    stages{
        stage('clonning'){
            steps{ 
               git url: 'git@github.com:kishorebittu3003/shopizer.git',
                   branch: 'daybuild'
           }
        }
    stage('manual_steps'){
        steps{
             sh 'git branch'
             sh 'pwd'
             sh 'ls'
             sh 'git checkout developer'
             sh 'git checkout realease'
             sh 'git branch -a'
             sh 'ls'
             //sh 'git merge developer --no-ff'
             //sh 'git push -u origin realease'
             //sh 'git log --oneline --all --graph --decorate'

            }
        }
    }
}