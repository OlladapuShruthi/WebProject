pipeline {
    agent any

    tools {
        // Make sure these names match your Jenkins Global Tool Config
        maven 'MAVEN'
        jdk 'DefaultJDK'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                git url: 'https://github.com/OlladapuShruthi/WebProject.git', branch: 'master'
            }
        }

        stage('Build & Package') {
            steps {
                echo 'Running Maven build...'
                // Use 'bat' on Windows instead of 'sh'
                bat 'mvn clean package'
            }
        }

        stage('Archive Artifact') {
            steps {
                echo 'Archiving WAR file...'
                archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}
