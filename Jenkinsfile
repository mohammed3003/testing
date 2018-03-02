pipeline {
    agent any
    stages {
        stage('Example') {
           
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} (<${env.BUILD_URL}|Open>)"
                sh "/bin/ping -c 5 google.com"
            }
        }
    }
    
}
