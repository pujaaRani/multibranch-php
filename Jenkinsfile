pipeline {
    agent any
    stages {
        stage('Checkout From Staging Branch') {
           
           steps {
           //checkout scmGit(branches: [[name: '*/staging']], extensions: [], userRemoteConfigs: [[credentialsId: 'puja-git-hub-cread', url: 'https://github.com/pujaaRani/multibranch-php.git']])
            git branch: 'staging', credentialsId: 'puja-git-hub-cread', url: 'https://github.com/pujaaRani/multibranch-php.git'
               
           }
        }
        stage('Deploy On Staging Environment') {
          when {
                branch 'staging'
            }    
          steps {
             sshagent(['new-test']) {
              sh 'ssh -o StrictHostKeyChecking=no root@3.111.31.231' 
              sh 'scp -r /var/lib/jenkins/workspace/multiple-branch-insingle-pipeline/* root@3.111.31.231:/var/www/html/'
              }
            }
        }
    }
}    
