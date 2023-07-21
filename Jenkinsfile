pipeline {
    agent any 
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    gitcheckout(
                        branch:"main"
                        url:"https://github.com/sriram182000/mrdevops_java_app.git"
                    )
                }
            }
        }
    }
}