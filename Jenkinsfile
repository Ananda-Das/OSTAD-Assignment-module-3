pipeline {
    agent {
        label 'ananda-class-node'
    }
    stages {
        stage('Git Clone') {
            steps {
              git branch: 'main', credentialsId: 'bbb6b639-a04d-4919-b88d-8f820755eec6', url: 'git@github.com:Ananda-Das/OSTAD-Assignment-module-3.git'
              echo 'Successfully Cloned the Repository'
            }
        }

        stage('Install'){
            steps {
                echo 'INSTALL Stage'
                sh 'npm install'
                echo 'Succesfully Installed'
            }
        }
        stage('Test'){
            steps {
                echo 'Test Stage'
                script {
                    try {
                        sh 'npm run check'
                        echo 'All test pass'
                    } catch (Exception e){
                        echo 'Test failed. Error' + e.getMessage()
                        error 'Test Failed'
                    }
                }
            }
        }
    }
}