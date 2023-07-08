@Library('jenkins-shared-library') _
pipeline {
    agent any 
     tools {
        maven "Maven3"
    }

    stages{

        stage('Git checkout') {
           
            steps {
                gitCheckout(
                        branch: "main",
                        url: "https://github.com/sriram182000/mrdevops_java_app.git"
                )
            }
        }
        stage('Unit Testing') {
            steps {
                script {
                    mvnunittest()
                }
            }
        }
        stage ('Integration Testing') {
            steps {
                script {
                    mvninttest()
                }
            }
        }
    }
}