pipeline {
    agent any 
    stages {
        stage('Npm install'){
            steps{
                sh '''
                cd /home/ec2-user/.jenkins/workspace/ang_clone/RideShare
                npm i
                '''
            }
        }
        stage('Build') { 
          steps {
                sh '''
                cd /home/ec2-user/.jenkins/workspace/ang_clone/RideShare
                ng build
                '''
          }
        }
        stage('Test'){
            steps{
                sh '''
                cd /home/ec2-user/.jenkins/workspace/ang_clone/RideShare
                npm run test-headless
                '''
            }
        }
        stage('Deploy'){
            steps{
                sh '''
                cd /home/ec2-user/.jenkins/workspace/ang_clone/RideShare
                 aws2 s3 cp --recursive ./dist s3://ang_clone/angular
                '''
            }
        }
    }
}