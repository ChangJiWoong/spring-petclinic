pipeline{
  agent any

  stages {
    // GitHub Clone
    stage('Git Clone') {
      steps {
          gut url: 'https://github.com/ChangJiWoong/spring-petclinic.git/', branch: 'main'
      }
    }
  }
}
