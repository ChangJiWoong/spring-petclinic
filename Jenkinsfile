pipeline{
  agent any

  tools{
    maven 'M3'
    jdk 'JDK21'
  }

  stages {
    // GitHub Clone
    stage('Git Clone') {
      steps {
          git url: 'https://github.com/ChangJiWoong/spring-petclinic.git/', branch: 'main'
      }
    }

    // Maven Build
    stage('Maver Build') {
      steps {
       sh 'mvn -Dmaven.test.failure.ignore=true clean package'
      }
    }
  }
}
