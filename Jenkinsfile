pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
        buildDiscarder logRotator(artifactDaysToKeepStr: '30', artifactNumToKeepStr: '50', daysToKeepStr: '', numToKeepStr: '')
    }
    
    stages {
        stage('Download from SCM') {
            steps {
                // Commands to build your project (e.g., compiling code)
                echo 'Continuous download is started...'
                git branch: 'main', url: 'https://github.com/ee212273/JND_Demo.git'
                // Example: sh 'mvn clean package'
            }
        }
        
        stage('Continuous Build stage ') {
            steps {
                // Commands to run tests
                echo 'Build by using maven...'
                sh 'mvn package'
                // Example: sh 'mvn test'
            }
        }
        
        stage('Deploy to container') {
            steps {
                // Commands to deploy your application
                echo 'Deploying the application in tomcat9 server...'
                //sh 'scp /var/lib/jenkins/workspace/Joynext_demo/webapp/target/webapp.war ubuntu@172.31.31.0:/var/lib/tomcat9/webapps/joynext.war'
                //sh 'scp /var/lib/jenkins/workspace/Joynext_demo/webapp/target/webapp.war ubuntu@172.31.31.0:/var/lib/tomcat9/webapps/webapp.war'
                // Example: sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline succeeded! Application is deployed.'
            // Additional actions upon successful pipeline execution
        }
        failure {
            echo 'Pipeline failed! Deployment aborted.'
            // Additional actions upon failed pipeline execution
        }
    }
}
