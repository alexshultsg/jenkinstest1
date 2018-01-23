pipeline {
    agent any
    node {
        echo "node..."
    }

 
    stages {
        stage("Init") {
            steps {
                echo "Init..."
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
