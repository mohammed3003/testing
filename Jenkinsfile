pipeline {

  agent {
    label ""
  }
  
  
  environment {
    FOO = "BAR"
  }
  
  stages {
    stage("first stage") {
      
              post {
                  always {
                    slackSend channel: '#general',
                         color: 'good',
                         message: "starting the build, pending your approval:"
                         }
            }
         
         input 'okay to proceed with stage 1:'

         steps {
     
        timeout(time: true, uint: 'MINUTES') {
          echo "We're not doing anything particularly special here."
          echo "Just making sure that we don't take longer than five minutes"
          echo "Which, I guess, is kind of silly."
          
          sh "/bin/ping -c 2 google.com" 
        }
      }
      
      post {
                  failure {
                    slackSend channel: '#general',
                         color: 'bad',
                         message: "The pipeline failed"
                         }

                   sucess {
                    slackSend channel: '#general',
                         color: 'good',
                         message: "The pipeline completed sucessfully"
                         }
                    }
 
        }

      }
   }
    
