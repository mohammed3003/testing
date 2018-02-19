pipeline {
    agent any
    stages {
        stage('Example') {
            post { always { slackSend channel: '#general', color: 'good', message: 'The pipeline ${currentBuild.fullDisplayName} ${env.JOB_NAME} has started....'}}
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} (<${env.BUILD_URL}|Open>)"
                sh "/bin/ping -c 5 google.com"
            }
        }
    }
    
    post {
        
                  failure {
                    slackSend channel: '#general',
                         color: 'danger',
                         message: "The pipeline ${env.JOB_NAME} ${env.BUILD_NUMBER} FAILED to complete sucessfully: (<${env.BUILD_URL}|Open>)"
                         }

                  success {
                    slackSend channel: '#general',
                         color: 'good',
                         message: "The pipeline ${currentBuild.fullDisplayName} completed successfully: (<${env.BUILD_URL}|Open>)"
                      
                    
                      input message: "Image ${WORDPRESS}:$TAG has been released to stage, please test and confirm..."
                      
                         }
            
                  
                     }
}
