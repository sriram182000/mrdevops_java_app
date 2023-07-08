@library('jenkins-shared-library') _
pipeline {
    agent any 

    stages{

        stage('Git checkout') {
           
            steps {
              
                script {
                   
                    gitcheckout(
                        branch: "main"
                        url: "https://github.com/sriram182000/mrdevops_java_app"
                    )
                }
            }
        }
    }
}