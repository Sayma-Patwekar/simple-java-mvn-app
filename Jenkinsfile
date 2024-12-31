pipeline {
    agent any
    tools {
        maven "mvn399"
    }
    stages {
        stage('mvn version'){
            steps{
                sh 'echo Print mvn version'
                sh 'mvn -v'
            }
        }
        stage('Build') {
            steps {
                //git branch: 'main', url: 'https://github.com/Sayma-Patwekar/simple-java-mvn-app.git'
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
            }

            // post {
            //     always {
            //         junit 'target/surefire-reports/*.xml'
            //     }
            // }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}