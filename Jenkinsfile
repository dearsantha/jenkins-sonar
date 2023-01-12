pipeline {
    agent any
tools
    {
    maven 'Maven 3.8.7'
        jdk 'jdk8'
        
}
    stages {
        stage('Build') {
            steps {
                 sh 'mvn clean package'
            }
        }
    }
}
