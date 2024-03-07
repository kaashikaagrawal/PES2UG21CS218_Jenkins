pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Define the Maven tool
                    def mvnHome = tool name: 'Maven', type: 'maven'
                    // Use the defined Maven tool
                    sh "${mvnHome}/bin/mvn clean install"
                }
                echo 'Build stage Successful'
            }
        }
        stage('Test') {
            steps {
                script {
                    // Define the Maven tool
                    def mvnHome = tool name: 'Maven', type: 'maven'
                    // Use the defined Maven tool
                    sh "${mvnHome}/bin/mvn test"
                }
                echo 'Test stage Successful'
                post {
                    always {
                        junit 'target/surefire-reports/*.xml'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Define the Maven tool
                    def mvnHome = tool name: 'Maven', type: 'maven'
                    // Use the defined Maven tool
                    sh "${mvnHome}/bin/mvn deploy"
                }
                echo 'Deployment Successful'
            }
        }
    }
    post {
        failure {
            echo 'Pipeline Failed'
        }
    }
}
