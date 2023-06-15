pipeline{
  agent any
  stages {
    stage('Build') {
        steps {
            sh 'mvn -f hello-app/pom.xml -B -DskipTests clean pavkage'
        }
        post {
            success {
                echo "Now Archiving the Artifacts..."
                archiveArtifacts artifacts: '**/*.jar'
            }
        }
     }
     stage('Test')
          steps {
              sh 'mvn -f hello-app/pom.xml'
          }
          post {
              always {
                    junit 'hello-app/target/surefire-reports/*.xml'
              }
          }
     }
  }
}
