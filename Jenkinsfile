pipeline{
    agent any
    environment {
         PATH = "$PATH:/usr/share/maven/bin"
    }
    stages{
        stage('Git Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/adeshbagale/webapp-edureka.git'
            }
        }
        stage('Build'){
            steps{
                 sh "mvn clean package"
            }
        }
        stage('Sonar Analysis'){
            steps{
                withSonarQubeEnv('sonarqube') {
                sh '''
                cd /var/lib/jenkins/workspace/web-app/
                mvn clean install
                mvn sonar:sonar
                '''
            }
            } 
        }
    }
}