@Library('my-shared-library') _
pipeline {
    agent any 
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    gitCheckout(
                        branch:"main",
                        url:"https://github.com/sriram182000/mrdevops_java_app.git"
                    )
                }
            }
        }
    }
}