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
            stage('Depoly to tomcat') {
                  steps {
                        curl -O http://localhost:8081/repository/siri/com/jdevs/CloudGen/4.0/CloudGen-4.0.war
                        cp http://localhost:8081/repository/siri/com/jdevs/CloudGen/4.0/CloudGen-4.0.war /opt/tomcat/webapps/CloudGen-4.0
               }
           }
  }
}
