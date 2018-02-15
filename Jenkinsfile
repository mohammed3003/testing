pipeline {
    agent any
    stages {
        stage('Example') {
            post { always { slackSend channel: '#general', color: 'good', message: 'The pipeline ${currentBuild.fullDisplayName} ${env.JOB_NAME} has started....'}}
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                sh "/bin/ping -c 5 google.com"
            }
        }
    }
    
    post {
        
                  failure {
                    slackSend channel: '#general',
                         color: 'bad',
                         message: "The pipeline ${currentBuild.fullDisplayName} FAILED to complete sucessfully."
                         }

                  success {
                    slackSend channel: '#general',
                         color: 'good',
                         message: "The pipeline ${currentBuild.fullDisplayName} completed successfully."
                         }
                     }
}
