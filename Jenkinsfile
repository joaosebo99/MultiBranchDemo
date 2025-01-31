pipeline { 
  
   agent any

   stages {
   
     stage('Checkout') { 
        steps { 
         bat('echo "Checkout code"')
        }
     }
     
     stage('Compile') { 
        steps { 
           bat('echo "compile application..."')
        }
      }

        stage('Review') { 
        steps { 
           bat('echo "Review application..."')
        }
      }

      stage('Test') { 
        steps { 
           bat('echo "Test application..."')
        }
      }
         stage("Package application") { 
         steps { 
           bat('echo "package application..."')
         }

     }

     stage("Deploy application") { 
          when {
                anyOf {
                    branch 'Dev'
                }
         }
         steps {
           script {
                        env.SAMPLE_USERNAME = input message: 'Please enter username:',
                                            parameters: [string(defaultValue: '',
                                                        description: 'Username',
                                                        name: 'Username')]
                        env.SAMPLE_PASSWORD = input message: 'Please enter password:',
                                            parameters: [password(defaultValue: '',
                                                        description: 'Password',
                                                        name: 'Password')]
                    }
           deploy('1.2.3')
         }

     }

  }
  
}

def deploy(version) {
  bat('echo "Deployment application for %SAMPLE_USERNAME%..."')
}

