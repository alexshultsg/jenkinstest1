pipeline {
    agent any
    stages {
        stage("Init") {
            steps {
                echo "Init..."
                env.JAVA_HOME='C:\\Program Files (x86)\\Java\\jre1.8.0_111'
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
