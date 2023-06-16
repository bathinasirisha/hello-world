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
                      sh 'git pull https://github.com/bathinasirisha/hello-world.git'
                      sh 'ls -la'
                      }
               }
            stage('excute maven') {
                  steps {
                        sh 'mvn clean'
                       sh  'mvn deploy -DaltDeploymentRepository=siri::default::http://localhost:8081/repository'

                        
                        }
               }
            stage('Deploy to Nexus') {
            steps {
               sh 'mvn deploy'
            }
        }
            stage('Depoly to tomcat') {
                  steps {
                       sh 'curl -O http://localhost:8081/repository/siri/com/jdevs/CloudGen/4.0/CloudGen-4.0.war'
                      sh 'cp http://localhost:8081/repository/siri/com/jdevs/CloudGen/4.0/CloudGen-4.0.war /opt/tomcat/webapps/CloudGen-4.0'
               }
           }
  }
}
