pipeline {
    agent {
        label 'ansible'
    }
    stages {
        stage('Checkout from git') {
            steps {
                sh 'rm -rf *'
                sh 'mkdir -p vector-role'
                checkout scmGit(branches: [[name: '*/main']], extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'vector-role']], userRemoteConfigs: [[credentialsId: 'd63b5ba6-728a-4a1c-881c-4dbfb6f3caa7', url: 'git@github.com:d1abel/devops-homeworks-vector-role.git']])
            }
        }
        stage('run test') {
            steps {
                dir('vector-role') {
                    sh 'molecule test'
                }
            }
        }
    }
}
