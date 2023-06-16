pipeline 
{
  agent any
  stages {
          stage('delete old repo') 
               {
                 steps {
                        sh 'rm -rf siri'
                        sh 'ls -la'
                        }
               }
    
           stage('clone')
               {
                steps {
                      sh 'git clone https://github.com/bathinasirisha/learnings.git'
                      sh 'ls -la'
                      }
               }
            stage('excute maven') {
                  steps {
                        sh 'mvn clean'
                        
                        }
               }
            stage('Deploy to Nexus') {
            steps {
               sh 'mvn deploy'
            }
        }
            stage('restart service') {
                  steps {
                        sh  'curl admin:raosiri2806'
               }
           }
  }
}
