pipeline {
    agent any
    stages{
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
                withCredentials([string(credentialsId: 'sonartoken', variable: 'sonartoken'), string(credentialsId: 'sonarhost', variable: 'sonarhost')]) {
                    sh '/opt/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=dbmanager -Dsonar.sources=. -Dsonar.host.url=${sonarhost} -Dsonar.token="${sonartoken}" -Dsonar.python.coverage.reportPaths=coverage.xml'
                }
            }
        }
    }
}