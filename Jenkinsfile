pipeline {
    agent any
    tools {
        maven "maven3"
        jdk "ORACLEJDK21"

    }
    stages {
        stage('Source Code Checkout'){
            steps{
                echo "Hello welcome to my pipeline"
            }

        }
        stage ('Code Compilation'){
            steps{
                sh 'mnv compile'
            }
        }
        stage('Testing '){
            steps{
                sh 'mvn test '
            }
        }
        stage('Trivy dependency scan'){
            steps{
                sh 'trivy fs --format table -o trivy-fs-report.html .'
            }     
        }
        stage('Sonarqube code Analysis')
            steps{
                sh 'mvn sonar:sonar'
            }
    }

}