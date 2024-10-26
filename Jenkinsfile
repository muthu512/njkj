pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone your GitHub repository
                git url: 'https://github.com/muthu512/njkj', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                bat 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Define paths
                    def buildJar = "C:\\Users\\Dell-Lap\\.jenkins\\workspace\\DeploySpringBoot\\target\\spring-boot-2-hello-world-1.0.2-SNAPSHOT.jar"
                    def deployFolder = "C:\\Users\\Dell-Lap\\Downloads\\Newfolder"
                    def deployJar = "${deployFolder}\\spring-boot-2-hello-world-1.0.2-SNAPSHOT.jar"

                    // Copy the JAR to the specified deployment folder
                    bat "copy /Y \"${buildJar}\" \"${deployJar}\""

                    // Run the JAR directly from the deployment folder
                    bat "start java -jar \"${deployJar}\""  // Removed port option
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
