pipeline {

    agent any

//	parameters {
//	    string(name: 'tomcat_dev', defaultValue: '', description: '')
//	    string(name: 'tomcat_prod', defaultValue: '', description: '')
//	}

    stages {
        stage("Init") {
            steps {
                echo "Init...Init..."
                bat 'set JAVA_HOME'
            }
        }
        stage("Build unix") {
        	when {
        	    expression {
					return isUnix()	      
        	    }
        	}

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
        stage("Build Windows") {
           	when {
        	    expression {
					return !isUnix()	      
        	    }
        	}
            steps {
                echo "Building windows..."
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
        stage("Deploy to Staging1") {
            steps {
                echo "Deploying1..."
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
