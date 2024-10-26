pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Use withCredentials to access Git credentials
                    withCredentials([usernamePassword(credentialsId: 'muthu512', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]) {
                        // Clone the repository using the provided credentials
                        bat "git clone https://${muthu512}:${512494}https://github.com/muthu512/njkj.gitt"
                    }
                }
            }
        }

        stage('Build') {
            steps {
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

                    // Run the JAR directly from the deployment folder with arguments
                    bat "start java -jar \"${deployJar}\" --spring.profiles.active=prod --server.port=1010"
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
