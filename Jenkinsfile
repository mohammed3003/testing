pipeline {
    agent any
    stages {
        stage('Example') {
            post { always { slackSend channel: '#general', color: 'good', message: 'The pipeline ${currentBuild.fullDisplayName} ${env.JOB_NAME} has started....'}}
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                sh "/bin/ping -c 5 google"
            }
        }
    }
    
    post {
        
                  failure {
                    slackSend channel: '#general',
                         color: 'danger',
                         message: "The pipeline ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>) FAILED to complete sucessfully."
                         }

                  success {
                    slackSend channel: '#general',
                         color: 'good',
                         message: "The pipeline ${currentBuild.fullDisplayName} completed successfully."
                         }
                     }
}
