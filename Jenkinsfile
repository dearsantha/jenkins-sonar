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
                -Dsonar.projectKey=jenkins-sonar \
                -Dsonar.host.url=http://13.233.117.201:9000/"
              }
            }
    }
  stage("Quality GAte Status check"){
	 timeout(time:1,unit:'HOURS'){
	     def qg = waitForQualityGate()
             if (qg.status != 'OK') {
	         error "pipeline aborted due to quality check failure: ${qg.status}"
	
}
}
}      
}
}
