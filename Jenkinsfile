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
// pipeline {
//     agent any

//     tools {
//         jdk 'DefaultJDK'   // Jenkins configured JDK
//         maven 'MAVEN'      // Jenkins configured Maven
//     }

//     environment {
//         TOMCAT_HOME = 'C:\\Apache\\tomcat9' // Windows Tomcat home path
//         EMAIL_RECIPIENT = 'olladapushruthi@gmail.com'
//     }

//     stages {
//         // -------------------
//         stage('Checkout') {
//             steps {
//                 echo 'Cloning project from GitHub'
//                 git 'https://github.com/OlladapuShruthi/Maven_Project.git'
//             }
//         }

//         // -------------------
//         stage('Build') {
//             steps {
//                 echo 'Cleaning and building the project with Maven'
//                 bat 'mvn clean package'
//             }
//         }

//         // -------------------
//         stage('Run Scripts') {
//             steps {
//                 echo 'Running custom scripts after build'
//                 // Example: run a shell script (Windows uses bat)
//                 bat 'echo Running post-build script...'
//                 // You can replace this with your actual scripts, e.g.,
//                 // bat 'scripts\\myScript.bat'
//             }
//         }

//         // -------------------
//         stage('Test') {
//             steps {
//                 echo 'Running unit tests'
//                 bat 'mvn test'
//             }
//             post {
//                 always {
//                     echo 'Publishing JUnit test results'
//                     junit '**/target/surefire-reports/*.xml'
//                 }
//             }
//         }

//         // -------------------
//         stage('Archive Artifacts') {
//             steps {
//                 echo 'Archiving build artifacts (JAR/WAR)'
//                 archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
//             }
//         }

//         // -------------------
//         stage('Deploy to Tomcat') {
//             steps {
//                 echo 'Deploying WAR to Tomcat'
//                 // Copy WAR file to Tomcat webapps folder
//                 bat """
//                 copy target\\*.war %TOMCAT_HOME%\\webapps\\
//                 """
//                 // Optionally restart Tomcat (Windows)
//                 bat """
//                 net stop Tomcat9
//                 net start Tomcat9
//                 """
//             }
//         }
//     }

//     // -------------------
//     post {
//         success {
//             echo 'Build Successful! Sending success email...'
//             mail to: "${EMAIL_RECIPIENT}",
//                  subject: "Jenkins Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
//                  body: "Good news! The Jenkins build ${env.JOB_NAME} #${env.BUILD_NUMBER} succeeded."
//         }
//         failure {
//             echo 'Build Failed! Sending failure email...'
//             mail to: "${EMAIL_RECIPIENT}",
//                  subject: "Jenkins Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
//                  body: "Oops! The Jenkins build ${env.JOB_NAME} #${env.BUILD_NUMBER} failed. Please check Jenkins logs."
//         }
//     }
// }
// pipeline {
//     agent any

//     stages {

//         stage('Checkout Code') {
//             steps {
//                 git 'https://github.com/lohithak28/week9maven-1.git'
//             }
//         }

//         stage('Build WAR') {
//             steps {
//                 bat "mvn clean package"
//             }
//         }

//         stage('Archive WAR') {
//             steps {
//                 archiveArtifacts artifacts: 'target/*.war', fingerprint: true
//             }
//         }

//         stage('Deploy to Tomcat') {
//             steps {
//                 bat '''
//                     copy target\\*.war C:\\tomcat9\\webapps\\ /Y
//                     net stop "Tomcat9"
//                     net start "Tomcat9"
//                 '''
//             }
//         }
//     }
// }
