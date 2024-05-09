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
        stage ('Application Build'){
            steps{
                sh 'mvn compile'
            }

        }
        stage ('Code Compilation'){
            steps{
                sh 'mnv test'
            }
        }
        stage('Testing '){
            steps{
                sh 'mvn checkstyle:checkstyle '
            }
        }
        stage('Checkstyle Analysis '){
            steps{
                sh 'mvn package '
            }
        }

        stage('Nexus Artifactory Upload'){
            steps {
                withMaven(globalMavenSettingsConfig: 'global-settings', jdk: 'ORACLEJDK21', maven: 'maven3', mavenSettingsConfig: '', traceability: true) {
                        sh "mvn deploy"
            }
        }
        stage('Trivy Dependency Scan'){
            steps{
                sh 'trivy fs --format table -o trivy-fs-report.html .'
            }     
        }
        stage('Sonarqube Code Analysis'){
            steps{
                sh 'mvn sonar:sonar'
            }
        }   
    }

}