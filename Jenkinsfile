pipeline{
    agent any
    environment {
         PATH = "$PATH:/usr/share/maven/bin"
    }
    stages{
        stage('Git Checkout'){
            steps{
                git branch: 'master', url: 'https://github.com/mitreid-connect/simple-web-app.git'
            }
        }
        stage('Build'){
            steps{
                 sh "mvn -B -DskipTests clean install"
            }
        }
        stage('Sonar Analysis'){
            steps{
                withSonarQubeEnv('sonarqube') {
                sh '''
                mvn sonar:sonar
                '''
            }
            } 
        }
    }
}
