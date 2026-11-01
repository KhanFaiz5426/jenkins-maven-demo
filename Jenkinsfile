
pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'tomcat-creds',
                        usernameVariable: 'TOMCAT_USER',
                        passwordVariable: 'TOMCAT_PASS'
                    )
                ]) {
                    bat '''
                    curl.exe --fail --show-error --user "%TOMCAT_USER%:%TOMCAT_PASS%" --upload-file "target\\jenkins-maven-demo-1.0-SNAPSHOT.war" "http://localhost:8145/manager/text/deploy?path=/jenkins-maven-demo&update=true"
                    '''
                }
            }
        }
    }
}
