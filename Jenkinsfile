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
