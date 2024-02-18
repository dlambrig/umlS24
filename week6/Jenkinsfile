pipeline {
  agent {
    kubernetes {
      // Define the pod template with container template
      containerTemplate {
            name 'gradle'
            image 'gradle'
            command 'sleep'
            args '30d'
        }
    }
  }
  
  stages {
    stage('Checkout code and prepare environment') {
      steps {
        git url: 'https://github.com/dlambrig/Continuous-Delivery-with-Docker-and-Jenkins-Second-Edition.git', branch: 'master'
        sh """
          cd Chapter08/sample1
          chmod +x gradlew
        """
      }
    }
    stage('Run pipeline against a gradle project - test branch') {
      when {
        not { branch 'main' }
      }
      steps {
         echo 'Unit test not main branch'
         sh """
           cd Chapter08/sample1; 
           ./gradlew test
         """
      }
    }
  }
}
