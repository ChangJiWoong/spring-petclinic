pipeline{
  agent any

  tools{
    maven 'M3'
    jdk 'JDK21'
  }
  environment{
      DOCKERHUB_CREDENTIALS = credentials('dockerCredential')
  }

  stages {
    // GitHub Clone
    stage('Git Clone') {
      steps {
          git url: 'https://github.com/ChangJiWoong/spring-petclinic.git/', branch: 'main'
      }
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
          docker build -t spring-petclinic:$BUILD_NUMBER .
          docker tag spring-petclinic:$BUILD_NUMBER changjiwoong/spring-petclinic:latest
          """
        }
      }
    }
   
    // Docker Login
    stage ('Docker Login and Push') {
      steps {
        sh """
        echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin
        docker push changjiwoong/spring-petclinic:latest
        """
        

      }
    }

    // Docker Image Remove
    stage ('Docker Image Remove') {
      steps {
        sh """
        docker rmi spring-petclinic:$BUILD_NUMBER
        docker rmi changjiwoong/spring-petclinic:latest
        """
      }
    }

    }
  }
      
  
  

