pipeline {
    agent any 

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code
                git 'https://github.com/muthu512/njkj.git'
            }
        }

        stage('Build') {
            steps {
                // Build the application
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                // Run tests
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Define the JAR file path from the Jenkins workspace after build
                    def jarFile = "C:\\Users\\Dell-Lap\\.jenkins\\workspace\\DeploySpringBoot\\target\\spring-boot-2-hello-world-1.0.2-SNAPSHOT.jar"
                    def targetDir = "C:\\Users\\Dell-Lap\\Downloads\\Newfolder"

                    // Ensure the target directory exists
                    bat "mkdir ${targetDir}"

                    // Copy the JAR file to the target directory
                    bat "copy ${jarFile} ${targetDir}"

                    // Change to the target directory and run the JAR
                    dir(targetDir) {
                        bat "start java -jar spring-boot-2-hello-world-1.0.2-SNAPSHOT.jar --server.port=1010"
                    }
                }
            }
        }
    }
}
