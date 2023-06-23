pipeline {
  agent any 
  tools {
    maven 'maven'
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
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@54.234.228.142:/prod/apache-tomcat-10.1.10/webapps/webapp.war'
              }      
           }       
    }

  }
}
      
      
