pipeline {
    agent any
    stages {
        stage("Init") {
            steps {
                echo "Testing..."
            }
        }
        stage("Build") {
            steps {
                echo "Building..."
                bat 'set JAVA_HOME C:\\Program Files (x86)\\Java\\jre1.8.0_111'
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
