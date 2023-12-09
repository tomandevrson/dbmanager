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
        stage('Sonar Scan'){
            steps{
                withCredentials([string(credentialsId: 'sonartoken', variable: 'sonartoken')]) {
                    sh 'sonar-scanner -DprojectKey=dbmanager -Dsonar.sources=. -Dsonar.host.url=http://192.168.0.56:9000 -Dsonar.token=sqp_8b84c0e88788049dd013d226ec8d50c4023b4edc -Dsonar.python.coverage.reportPaths=coverage.xml'
                }
            }
        }
    }
}