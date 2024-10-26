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
                    // Define the JAR file path
                    def jarFile = "C:\\Users\\Dell-Lap\\.jenkins\\workspace\\DeploySpringBoot\\target\\spring-boot-2-hello-world-1.0.2-SNAPSHOT.jar"

                    // Change the working directory and run the JAR from the target folder
                    dir('C:\\Users\\Dell-Lap\\Downloads\\Newfolder') {
                        bat "start java -jar ${jarFile} --server.port=1010"
                    }
                }
            }
        }
    }
}
