pipeline {
    agent any
    stages{
        stage('Preparation'){
            steps{
                git 'https://github.com/tomandervson/dbmanager.git'
            }
        }
        stage('Code Coverage'){
            steps{
                sh 'coverage run -m pytest'
            }
        }
        stage('XML Creation'){
            steps{
                sh 'coverage xml'
            }
        }
    }
}