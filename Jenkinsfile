pipeline {
    agent any

	parameters {
	    string(name: 'tomcat_dev', defaultValue: '', description: '')
	    string(name: 'tomcat_prod', defaultValue: '', description: '')
	}

	triggers {
	    pollSCM('* * * * *')
	}


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
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }
        stage("Deploy to Staging") {
            steps {
                echo "Deploying..."
            }
        }
        stage("Deploy to Production") {
            steps {
            	timeout( time:5, unit:'DAYS') {
                	input message: 'Approve PRODUCTION deployment?'                 
                }

                echo "Deploying to production..."
            }
            post {
                success {
                	echo "Deploying to production... SUCCESS"    
                }
                failure {
                    echo "Deploying to production... FAILED"
                }
            }
        }
    }
}
