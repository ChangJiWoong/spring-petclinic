pipeline{
  agent any

  stages {
    // GitHub Clone
    stage('Git Clone') {
      steps {
          git url: 'https://github.com/ChangJiWoong/spring-petclinic.git/', branch: 'main'
      }
    }
  }
}
