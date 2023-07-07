pipeline {
    agent any 
    stages{
        stage('Git checkout') {
            steps {
                script {
                    git branch: 'main', credentialsId: 'Git_checkout', url: 'https://github.com/sriram182000/mrdevops_java_app.git'
                }
            }
        }
    }
}