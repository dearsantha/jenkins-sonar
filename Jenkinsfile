pipeline {
    agent any
    stages {
         stage ('Build') {
            steps {
                echo 'This is a minimal pipeline.'
                sh 'mvn clean package'
            }
             stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
