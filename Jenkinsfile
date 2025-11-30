pipeline {
  agent any

  tools {
    maven 'MAVEN'  
    jdk 'DefaultJDK'  
  }

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/OlladapuShruthi/WebProject.git', branch: 'master'
      }
    }

    stage('Build & Test') {
      steps {
        // Use bat instead of sh on Windows
        bat 'mvn clean test'
      }
    }

    stage('Package') {
      steps {
        bat 'mvn clean package'
      }
    }

    stage('Archive Artifact') {
      steps {
        archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
      }
    }
  }

  post {
    always {
      junit '**/target/surefire-reports/*.xml'
    }
  }
}
