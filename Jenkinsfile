pipeline {
    agent any
    tools {
        maven "maven3"
        jdk "ORACLEJDK21"

    }
    stages {
        stage('Declarative Checkout SCM'){
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
        stage('Checkstyle Analysis '){
            steps{
                sh 'mvn checkstyle:checkstyle '
            }
        }
        stage('Trivy Dependency Scan'){
            steps{
                sh 'trivy fs --format table -o trivy-fs-report.html .'
            }     
        }
        stage('Sonarqube Code Analysis')
            steps{
                sh 'mvn sonar:sonar'
            }
    }

}