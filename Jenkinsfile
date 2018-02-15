pipeline {
    
    agent none
        
    stages {
        stage('Build') {
            agent { 
                label ""
                }
            }
            steps {

                post {
                  always {
                    slackSend channel: '#general',
                         color: 'good',
                         message: "test job started"
                         }
                    }

                    script {
                         sh "ping -c 5 google.com"
                         echo "Complete!"
                       }
              
                 }

               post {
                  sucess {
                    slackSend channel: '#general',
                         color: 'good',
                         message: "test job completed"
                         }

                  failure {
                    slackSend channel: '#general',
                         color: 'bad',
                         message: "test job failed"
                         }       
                    

                    }   

             }

        }
