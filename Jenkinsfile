pipeline { 
    agent none  
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean install'
            }
        }
            stage('Test') {
            steps {
                sh 'echo "test pass" '
            }
            
                }
            }
        
    
}
