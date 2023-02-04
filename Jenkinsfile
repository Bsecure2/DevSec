pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }

    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }

   stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['Jenkins']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@100.25.167.11:/DevSecOps/apache-tomcat-9.0.71/webapps/webapp.war'
              }      
           }       
    }
    

    }
}
