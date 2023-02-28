pipeline {
    agent {
  label 'makec'
    }
    stages{
        stage('get code') {
            steps{
                git branch: 'main', url: 'https://github.com/Rajeshwarisg94/Cfiles.git'
            }
        }

        stage('check main and makefile') {
            steps{
                sh '''
                echo "$(pwd)"
                if [ -f main.c ] && [ -f Makefile ];then
                echo "required files exists"
                else
                echo "files does not exists"
                exit 1
                fi
             '''
           }
        }

        stage('build') {
            steps{
                sh '''
                    make
                '''
            }
        }

        stage('test'){
            steps{
                sh 'echo "this is testing stage"'
            }
        }
        stage('save atrifact'){
            steps{
                sh 'scp -v -o StrictHostKeyChecking=no ABC.exe ubuntu@172.31.2.64:/home/ubuntu/cbuilds/ABC_$(date +%d_%m_%Y_%H_%M_%S).exe'
            }
        }

}
}
