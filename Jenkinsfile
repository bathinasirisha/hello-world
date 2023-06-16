pipeline 
{
  agent any
  stages {
          stage('delete old repo') 
               {
                 steps {
                        sh 'ssh sirisha@34.28.163.80 rm -rf siri'
                        sh 'ssh sirisha@34.28.163.80 ls -la'
                        }
               }
    
           stage('clone')
               {
                steps {
                      sh 'ssh sirisha@34.28.163.80 git clone https://github.com/bathinasirisha/learnings.git'
                      sh 'ssh sirisha@34.28.163.80 ls -la'
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
