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
    // Docker Image 생성
    stage('Docker Image Build') {
      steps{
        dir("${env.WORKSPACE}") {
          sh """
          docker build -t changjiwoong/spring-petclinic:$BUILD_NUMBER .
          docker tag changjiwoong/spring-petclinic:$BUILD_NUMBER changjiwoong/spring-petclinic:latest
          """
        }
      }
    }
   
    
    
  }
}
