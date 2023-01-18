pipeline { 
    agent any 
    tools {
    maven "maven"
  }
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
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
        stage('sonar quality check'){
            steps{
                withSonarQubeEnv('sonar'){
                    sh "mvn sonar:sonar \
                    -Dsonar.login=admin \
                    -Dsonar.password=1111 \
  -Dsonar.projectKey=jenkins-pipeline-sonarQube \
  -Dsonar.host.url=http://15.206.186.20:9000 \"
                }
            }
    }
}
}
