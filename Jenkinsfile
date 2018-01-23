pipeline {
    agent any

    stages {
        stage("Init") {
            steps {
                echo "Init..."
                bat 'set JAVA_HOME'
            }
        }
        stage("Build") {
            steps {
                echo "Building..."
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts 'target/*.jar'
                }

            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying..."
            }
        }
    }
}
